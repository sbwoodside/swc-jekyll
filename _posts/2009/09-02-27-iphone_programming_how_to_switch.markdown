---
layout: post
title: 'iPhone programming: how to switch to a landscape view at the moment of your choosing'
---


Maybe someday, Apple will make it easy to rotate manually into a landscape view. But right now it's been causing me enormous headache with hideous frames issues. Running an app in landscape the whole time is easy, but doing just some views in landscape is insane, especially if you're trying to switch while in the middle of a navigation controller.

However I've found an easy solution which is to use a new window. Just reset the whole view problem. You can then fake out the navigation bar using the method of your preference. Here's the bare bones. For me, I'm going from a tableView, click on an item and get a "results view".

<pre>// In ResultsListController, a UITableView delegate:<br />- (void)tableView:(UITableView *)tableView didSelectRowAtIndexPath:(NSIndexPath *)indexPath {<br />&#160; ResultsViewController * resultsViewController = [[[ResultsViewController alloc] initWithNibName:@"ResultsViewController" bundle:nil] autorelease];<br />&nbsp; resultsViewController._recordIndex = indexPath.row;<br />&nbsp; UIWindow * window = [[UIWindow alloc] initWithFrame:[[UIScreen mainScreen] bounds]]; // this is a leak!<br />&nbsp; window.backgroundColor = [UIColor redColor]; // just for debugging<br />&nbsp; [window addSubview:resultsViewController.view];<br />&nbsp; [window makeKeyAndVisible];<br />}</pre>

Now ResultsViewController has its own NIB, and the view is set to be sideways in IB.

<pre>// In ResultsViewController<br />- (void)viewWillAppear:(BOOL)animated; {<br />  // First rotate the screen:<br />&nbsp; [UIApplication sharedApplication].statusBarOrientation = UIInterfaceOrientationLandscapeRight;<br />  // Then rotate the view and re-align it:<br />&nbsp; CGAffineTransform landscapeTransform = CGAffineTransformMakeRotation( degreesToRadian(90) );<br />&nbsp; landscapeTransform = CGAffineTransformTranslate( landscapeTransform, +90.0, +90.0 );<br />&nbsp; [self.view setTransform:landscapeTransform];<br />}<br /><br />// Connect your "back" button in the results view to this:<br />- (IBAction)back:sender; {<br />  // return screen rotation to normal:<br />  [UIApplication sharedApplication].statusBarOrientation = UIInterfaceOrientationPortrait;<br />  // Get rid of the window, and the "normal" window will re-appear from underneath<br />  self.view.window.hidden = YES;<br />  [self.view.window resignKeyWindow];<br />}</pre>

Easy as cake!

UPDATE: There's follow-up Q&amp;A on the <a href="http://www.iphonedevsdk.com/forum/iphone-sdk-development/3219-force-landscape-mode-one-view-new-post.html">iphonedevSDK forums</a>.
