---
layout: article
title: "Nginx with passenger"
date: 2013-06-06 22:01:28 +0000
image: /assets/img/NGINX-328x220.jpg
---

After setting up Nginx, I wanted to test how ruby on rails with passenger is on it.

So basically I have had a lot of fun trying to get passenger working. In short, you have to reinstall Nginx with passenger support. To do this I had to remove it via apt and then followed this tutorial:

https://www.digitalocean.com/community/articles/how-to-install-rails-and-nginx-with-passenger-on-ubuntu

You start off by installing rvm and ruby gems then use the passenger installer to setup nginx. What annoyed me is that it installs to /opt by default, you can change this but since I am used to using apt for 80% of things I like things to be in /etc. Anyway! Once I had installed it to /opt I disocvered that all configs were different, no biggie but it took a little while to get my setup right again.

Now for the fun part, in each virtual host(if you even called them that on nginx) you simply add ‘passenger_enable on’ and we get nice speedy(imo) rails.

I have tested this with my install of gitlab and although it took a while when starting up it is very fast now, yay!
Over all I am really liking Nginx, everything from it’s lighting fast response times to the configs, actually really really like the configs as they are written in a C styles

My next adventure is trying to get a old rails app working, I have attempted this a few times but never got very far. I am hoping with my new found knowledge of ruby/rvm along with nginx I can finally get it working again.
