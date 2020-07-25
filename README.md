# 301-Redirect-using-.htaccess-file

The 301 Redirect or status code 301 Moved Permanently means a webpage is moved permanently from the old URL to a new URL. It will redirect a visitor and search engine to the new URL once they type the old URL in the browser or click from the search engine result page.

How to setup it and why it is necessary, visit the fulll blog post at https://bit.ly/2ZZsMHq
======================

Few way of doing 301 Redirects in .htaccess are:

1) Redirect a single old page to a new page

Redirect 301 /the-old-page.html /a-new-page.html


2) Migrate and Redirect your old domain to new domain

RewriteEngine on 

RewriteCond %{HTTP_HOST} ^oldsite.com [NC,OR] 

RewriteCond %{HTTP_HOST} ^www.oldsite.com [NC] 

RewriteRule ^(.*)$ https://newsite.com/$1 [L,R=3]



3) Redirect whole domain from HTTP to HTTPS

RewriteEngine On 

RewriteCond %{HTTPS} off 

RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301] 



4) Redirect whole domain from non-www to www (and reverse)

RewriteEngine on 

RewriteCond %{HTTP_HOST} ^example.com [NC] 

RewriteRule ^(.*)$ http://www.example.com/$1 [L,R=301,NC] 



5) Redirect whole domain from both non-www to www and HTTP to HTTPS

RewriteEngine On 

RewriteCond %{HTTP_HOST} !^www\. [NC] 

RewriteRule ^ https://www.%{HTTP_HOST}%{REQUEST_URI} [L,R=301] 

RewriteCond %{HTTP:X-Forwarded-Proto} !https 

RewriteCond %{HTTPS} off 

RewriteRule ^ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301] 



For more details, visit: https://bit.ly/2ZZsMHq
=======================
