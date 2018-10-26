---
layout: post
title: "A year with wordpress"
date: 2013-04-12T21:26:59+00:00
image: /content/uploads//2013/04/wordpress-logo.png
---

It has been one year since I started developing with Wordpress so I though I would write about a year working with it. Topics I will be covering are theme and plugin creation, my experience with 3rd party plugins, which ones I would recommend and which ones I would travel half way around the world to avoid.

<p>Prior to Wordpress I developed my own cms' they were build for purpose and never had reusability in mind. Website to website I would recreate the admin system, making bespoke solutions. Basically in the end it wasn't working out. I played around with joomla and other various tools but found them restricting.</p>
<p>Then I was introduced to Wordpress when I started at Forepoint Ltd. We use wordpress to create bespoke solutions for our clients. When I joined we falling into all the same traps, creating code over and over and over.</p>
<p>By this time in my development career I was sick of it all so I devised a plan of action. I updated the base wordpress theme we were using to include a smart and effective way of hooking into functionality, this can be viewed on <a href="https://github.com/forepoint/Forepoint-WP-Framework">github</a>. </p>
<p>The base of it all works from static classes, note the init hook name matches the method name on the class</p>
[php]add_action( 'init', array( 'APLConfig', 'init' ) );[/php]
<p>Now inside the class the public init method calls various private methods</p>
[php]
public static function init() {
    APLConfig::_enable_post_thumbnails( )
}
private static function _enable_post_thumbnails( ) {
    add_theme_support( 'post-thumbnails' );
}
[/php]
<p>The plugin was nothing more than a collection of a few helpful functions and basic rebranding of Wordpress. After creating this system and testing it on a few website we recreated the cms plugin from the ground up using the new class structure, which has existed for around 6 months now and has been used on multiple websites and plugins and seems to be holding up very well!</p>
<p>Whilst fixing our development proceses, I have found myself hitting my head against the wall and most recently thanks to Elliot Condom, create of the ACF plugin, who has change the way his plugin works thanks to Wordpress kicking off but less about that and more about the problem I have with Wordpress. Wordpress is an amazing tool, I love the template system and the hook system, they are brilliant. However, there are some parts of Wordpress that really do make me want to cry, ranging from simple inconsistencies (get_permalink) to major furkups, which granted is due to the vast number of developers that work on it.</p>
<h2>Themes</h2>
<p>Themes are a brilliant way to restyle your content, however we do not build themes at Forepoint, we build solutions. Basically meaning you could not you the themes we create in any other context, they are built to match the requirements of the website and nothing more.</p>
<p>The problem I have with the Wordpress theme system is the lack of A MVC relationship, having use template systems like Smarty in the past I found Wordpress get's in the way of allowing you to utilise any other but it's own template system, which I really do miss. This again comes back to Wordpress primarily being designed for blogging, there is no need for a controller when all you need to output is a few templates tags.</p>
<p>I do want to explore this matter though, if I find a worthy solution I will post about it.</p>
<h2>Plugins</h2>
<p>Since starting at Forepoint I have created many many plugins, starting from a small content rater plugin all that way up to a plugin that converts Wordpress into a full online dataroom.</p>
<p>Again thanks to our class/hook system, creating plugins is nice and maintainable. No much I can say about create plugins at this level, I will do a write up about plugins I have created soon.</p>
<p>What can be said is that when creating plugins, Wordpress' hook system really comes into it's own not only for linking into the Wordpress core but creating hooks in your own plugins so they are as flexible as a rubber hose!</p>
<p>Now I guess I better talk about some plugins</p>
<h3>Recommended plugins</h3>
<p>Advanced custom fields - Wordpress would simply not be what it is without ACF, create plugin check it out</p>
<p>WP better security - Just get it you security nut</p>
<p>AJAX Thumbnail Rebuild - Very useful plugin, rebuilds your image library with all the custom image sizes.</p>
<h3>Avoid!</h3>
<p>Instead of listing every plugin on Wordpress I thought it would be better to leave you with this idea, why use someone else's code if it is worst that your own? I can guarantee that most of the plugins you have installed or would like to install you can rewrite better, so why not do it? Eh? Just stop being lazy and write some good code!</p>
<p>With one year down and many more in the future I can only hope that the Wordpress team keep up the great work and for god's sake sort out those my todo list before I weep to death.</p>
