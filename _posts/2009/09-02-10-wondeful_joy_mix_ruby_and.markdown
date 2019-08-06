---
layout: post
title: Wondeful joy! Mix Ruby and Objective-C with MacRuby
image: macruby.png
---


How great is this. You can use any language you want in your MacRuby projects. Want to add in some code you already wrote in Objective-C++? No problemo!

Check out the cool screenshot below which shows everything in action! (You might have to click on the full post view to get the picture).

Also, you might be wondering how to get full bi-directional bridge going on between Ruby and Objective-C/Cocoa. In otherwords, how do you call/access/include/import/require your own Objective-C classes from Ruby and your Ruby objects from Objective-C? It's actually done sort of automagically. If you have a Ruby class Foo and a ObjC class Bar...

<em>(You seem to have to use NSClassFromString(@"FooController") to avoid getting a linker error. Apparently the bridge is not yet running at compile/link time. Also, you (seem to) have to type your bridged objects to id in ObjC, although maybe there's a way around both those limitations that I don't know about yet.)</em>

<pre># Foo.rb<br />class Foo<br />  def foo<br />    puts 'FOO'<br />    bar = Bar.new<br />    puts bar.bar<br />  end<br />  def baz<br />    return "BAZ"<br />  end<br />end<br /><br />// Bar.h<br />#import &lt;Cocoa/Cocoa.h&gt;<br />@interface Bar : NSObject {<br />}<br />- (NSString*)bar;<br />@end<br /><br />// Bar.m<br />#import "Bar.h"<br />@implementation Bar<br />- (NSString*)bar; {<br />  id foo = [[NSClassFromString(@"FooController") alloc] init];<br />  NSLog(@"%@", [foo baz]);<br />  return @"BAR";<br />}<br />@end</pre>

And you will get this output when you call Foo.foo:

<pre>FOO<br />2009-02-10 02:46:28.017 Untitled[37257:10b] BAZ<br />BAR</pre>

Boing boing boing! Enjoy!!!!
