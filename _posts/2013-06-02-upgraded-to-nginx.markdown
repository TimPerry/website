---
layout: post
title: "Upgraded to Nginx"
date: 2013-06-02T18:48:14+00:00
image: /content/uploads//2013/06/NGINX.jpg
---

After looking into alternative solutions for work, I have switched to Nginx.

<p>I am now using Nginx and Apache2 on my server and love it!</p>
<p>Nginx is setup as a reverse proxy, this means that Nginx does not actually process the content it just hands it off to Apache. Then why use Nginx at all? Well because it rocks! It can server 10,000 users with just 10Mb of ram, something Apache just can't do due to the way it handles connections. Ok then, why do we need Apache? Unfortunately Nginx cannot natively handle PHP, it is designed to server static content.</p>
<p>This means you have a few options:</p>
<ul>
<li>Use FastCGI</li>
<li>Use Apache with FastCGI</li>
<li>Use Apache wtih mod_php</li>
</ul>
<p>I have gone with the last options, Apache along with mod_php works perfectly so why change that.</p>
<p>Now onto the install, after playing around all night I have found out that you can swap over from Apache to a reverse proxy setup very quickly:</p>
<ul>
<li>Change Apache to listen on port 8080</li>
<li><span style="line-height: 13px;">Install Nginx</span></li>
<li>Setup Nginx on port 80</li>
<li>Configure Nginx default site</li>
</ul>
<p>Here is the config I am currently using for default</p>
<pre>[c]
server {

        listen 80;
        index index.php;

        rewrite /wp-admin$ $scheme://$host$uri/ permanent;
        rewrite ^(.*) $scheme://www.$host$uri/ permanent;

        location = /favicon.ico {
                log_not_found off;
                access_log off;
        }

        location = /robots.txt {
                allow all;
                log_not_found off;
                access_log off;
        }

        location ~ /. {
                deny all;
        }

        location ~* /(?:uploads|files)/.*.php$ {
                deny all;
        }

        location / {
                proxy_pass http://127.0.0.1:8080;

                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-For $remote_addr;
                proxy_set_header Host $host;
        }

}
[/c]</pre>

<p>All done! I will let you know how I get on, next I will be setting up passenger on Nginx to see if performance for Rail apps improves as I have found them to be very slow on Apache.</p>
