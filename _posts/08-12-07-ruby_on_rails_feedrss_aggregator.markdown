---
layout: post
title: Ruby on Rails Feed/RSS Aggregator (35 lines)
---


I wrote myself a feed aggregator for my front page. And... voila! I'm finally satisfied with it to post it.

<blockquote>

Update: I've now published this as a complete standalone rails app on <a href="http://github.com/sbwoodside/portal">github/sbwoodside/portal</a>. The important bits are app/controllers/portal_controller.rb and config/config.yml.

</blockquote>

For me I run this as a standalone rails app, separately from my weblog. You could do that (and redirect requests to / or /index.html with Apache or nginx/etc. Or you could integrate it into your own app. Up to you.

Features:

<ul><li>Will aggregate ANY feed, no matter how badly mangled by the creators, using <a href="http://rubyforge.org/projects/feedtools/">FeedTools</a> (I also tried feed_normalizer and simple rss but they're not as good)</li><li>Deals with slowness of downloading feeds, RSS, etc., and <a href="http://www.germane-software.com/software/rexml/">REXML</a> by caching</li><li>Deals with need to recache using elegant http/cron periodic system</li><li>Display the feeds in a facebook-like news feed format, sorted by dated.</li><li>You can easily re-label the feeds, add and renew feeds (in the code)</li><li>Only 35 lines of controller code!</li></ul>

The heart of it is the controller, obviously. The best thing? It's only one page of code! Ruby rocks!

<pre>require 'feed_tools'<br /><br />class PortalController &lt; ApplicationController<br />  layout 'site'<br />  # Instructions: 1. Change @@secret. 2. Add a cron job to regularly call /?recache=yes&amp;secret=XXXXXXX<br />  # This is a feed aggregator that uses FeedTools because it handles practically any feed.<br />  # But FeedTools is super slow in every way so this aggregator stops using it as soon as possible.<br />  # TODO add XML feed output<br />  <br />  @@secret = "change_this" # change this to protect your site from DoS attack<br />  # The array of feeds you want to aggregate. If you change this then manually delete the whole cache.<br />  @@uris = ['http://simonwoodside.com:8080/posts/rss', 'http://simonwoodside.com/comments/rss',<br />            'http://semacode.com/posts/rss',<br />            'http://api.flickr.com/services/feeds/photos_public.gne?id=20938094@N00&amp;lang=en-us&amp;format=rss_200',<br />            'http://api.flickr.com/services/feeds/activity.gne?user_id=20938094@N00']<br />  # A map between the "official" feed titles in the XML, and the titles you want to show when rendered.<br />  @@title_map = { "Simon Says" =&gt; "Simon Says:", "Simon Says: Comments" =&gt; "Simon Says comment:",<br />                  "Uploads from sbwoodside" =&gt; "Flickr picture:", "Semacode" =&gt; "Semacode blog post:",<br />                  'Comments on your photostream and/or sets' =&gt; 'Flickr comment:' }<br />  <br />  def index<br />    if params[:recache] and @@secret == params[:secret]<br />      cache_feeds<br />      expire_fragment(:controller =&gt; 'portal', :action =&gt; 'index') # next load of index will re-fragment cache<br />      render :text =&gt; "Done recaching feeds"<br />    else<br />      @aggregate = read_cache unless read_fragment({})<br />    end<br />  end<br />  <br />private<br />  # This will replace cached feeds in the DB that have the same URI. Be careful not to tie up the DB connection.<br />  def cache_feeds<br />    puts "Caching feeds... (can be slow)"<br />    feeds = @@uris.map do |uri|<br />      feed = FeedTools::Feed.open( uri )<br />      { :uri =&gt; uri, :title =&gt; feed.title, <br />        :items =&gt; feed.items.map { |item| {:title =&gt; item.title, :published =&gt; item.published, :link =&gt; item.link} } }<br />    end<br />    feeds.each { |feed|<br />      new = CachedFeed.find_or_initialize_by_uri( feed[:uri] )<br />      new.parsed_feed = feed<br />      new.save!<br />    }<br />  end<br />  # Make an array of hashes, each hash is { :title, :feed_item }<br />  def read_cache<br />    @@uris.map { |uri|<br />      feed = CachedFeed.find_by_uri( uri ).parsed_feed<br />      feed[:items].map { |item| {:feed_title =&gt; @@title_map[feed[:title]] || feed[:title], :feed_item =&gt; item} }<br />    } .flatten .sort_by { |item| item[:feed_item][:published] } .reverse<br />  end<br />end</pre>

It's actually pretty simple but it took me a while to get the balance just right. What you need to do is set up a cron job or other repetitive task that does an HTTP load on http://mywebsite.com/?recache=yes&amp;secret=XXXXXXXX ... every once in a while. You can use wget or curl, or whatever. You might want to recache every minute, five minutes, hour, whatever. Since it's done as a part of the controller there's no nonsense about running backgroundRB, RubyCron and all the other nonsense at <a href="http://wiki.rubyonrails.org/rails/pages/HowToRunBackgroundJobsInRails">HowToRunBackgroundJobsInRails</a>. Yay!

Here's the view:

<pre><br />&lt;div id="feed-stream"&gt;<br />  &lt;% cache do %&gt;<br />    &lt;%<br />      lastday = -1<br />      @aggregate.each do |item| %&gt;<br />        &lt;div class="item"&gt;<br />        &lt;%<br />          mydate = item[:feed_item][:published].getlocal<br />          if mydate.yday != lastday<br />            %&gt;&lt;div class="item_details"&gt;&lt;p style="text-align:right"&gt;&lt;%= mydate.strftime('%A, %B %e') %&gt;&lt;/p&gt;&lt;/div&gt;&lt;%<br />            lastday = mydate.yday<br />          end<br />        %&gt;<br />          &lt;div class="item_content"&gt;<br />            &lt;%= item[:feed_title] %&gt;<br />            &lt;a href="&lt;%= item[:feed_item][:link] %&gt;"&gt;&lt;%= item[:feed_item][:title] %&gt;&lt;/a&gt;<br />          &lt;/div&gt;<br />        &lt;/div&gt;<br />    &lt;% end %&gt;<br />  &lt;% end %&gt;<br />&lt;/div&gt;</pre>

My cache is all Hashes. I don't cache the FeedTools object because I discovered that even after FeedTools has parsed your feed, accessing the supposedly "final" data is incredibly slow (like maybe 10x or 100x slower than a hash).

Here's the model:

<pre><br />require 'feed_tools'<br />class CachedFeed &lt; ActiveRecord::Base<br />  validates_presence_of :uri, :parsed_feed<br />  validates_uniqueness_of :uri<br />  serialize :parsed_feed, Hash # note that if this exceeds a certain KB size, it will likely fail (thinking it's a String)<br />end</pre>

And the migration:

<pre><br />class CreateCachedFeeds &lt; ActiveRecord::Migration<br />  def self.up<br />    create_table :cached_feeds do |t|<br />      t.column :uri, :string, :limit =&gt; 2048<br />      t.column :parsed_feed, :text, :limit =&gt; 128.kilobytes # use for serialized object<br />      t.timestamps<br />    end<br />  end<br /><br />  def self.down<br />    drop_table :cached_feeds<br />  end<br />end</pre>

Well, that's all you need. When I started out to make this I thought I'd find a simple example out there but there wasn't anything. It turns out that there's a number of interesting challenges ‰ÛÓ picking a parser to deal with difficult feeds, XML, and malformatted XML... to deal with caching ... to deal with background processing. Took me a while to get it all just right.

It powers my own front page ... consider to be under standard ruby open source license. As the vending machine says: Share And Enjoy!
