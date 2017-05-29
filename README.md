## KatWeb
Welcome to KatWeb HTTP Server!
KatWeb is a modern HTTPS server designed for the 21st century.
Made in 100% Golang, currently in very early beta.
**PLEASE DO NOT USE THIS IN PRODUCTION, ITS NOT FINISHED!!!**

## File System Structure
- /html/ - Document root of server.
- /ssl/ - Server HTTPS certificates.
- /error/ - Server error pages.
- /conf.json - Server config file.

## Simple HTTP Cache
KatWeb comes with a built in HTTP Cache that can be useful for sending files from other websites through your server!
- To use it, you create a file called [filename].txt in the /cache folder.
  * Example : If you want to make your file called example.svg, you make a file named example.svg.txt
- Then, you put the link to the original source in the txt file.
  * Example : If you want meow.png to show a nyan cat gif, you put the link to the gif (http://kittyhacker101.tk/Static/Card.svg) in example.svg.txt.
- Now, you can view your stuff through /cache!
  * Example : To see example.svg, you can open localhost/cache/example.svg.txt in your browser.

## Dynamic Content Control
KatWeb comes with a built in system to serve different content depending on various factors.
- You can use this to send content differently by domain!
  * Just create a new folder with the domain name in the / folder (not /html, the layer below it). Then put your content in there!

## Config Options
- keepAliveTimeout - The max length of time a keep-alive connection can stay open in seconds. Must be greater than zero!
- cachingTimeout - How many hours you want the files sent by the web-server to be cached in the browser. Setting this to zero will disable caching.
- hsts - Forces all browsers to use HTTPS for your website. Requires a valid HTTPS cert.
  * enabled - If HSTS should be enabled, requires a valid HTTPS cert.
  * includeSubDomains - If HSTS should effect subdomains, must be enabled for preload to work.
  * preload - If your site's HSTS rule should be preloaded into the preload list. Once you are in the preload list, you can't get out of it easily!
- https - If you wish to have an encrypted connection.
- nosniff - Prevents web browsers from sniffing away content types.
- sameorigin - Prevents other web-sites from stealing your content using iframes.
- gzip - HTTP compression for files. Keep this on unless you are attempting to host on a Raspberry Pi Zero :P
- dyn - Dynamic content control. Directions below
  * serving - Serve content differently by domain. Non-configured domains default to /html/
  * cache - Caches content rules. If enabled, the server must be restarted for any content rules to change.
- silent - Don't log anything. Also disables most error checking, so be careful!
- hcache - Simple HTTP Cache. Directions below
  * enabled - If Simple HTTP Cache should be enabled.
  * updates - How often the HTTP Cache should update it's files in seconds.
- name - The server name sent in the "Server" HTTP Header.

Changing conf options requires a server restart to take effect.

## Current and Planned Features 
- [x] SSL Support
- [x] HSTS Support
- [x] JSON Config Files
- [x] HTTP/2 and Keep-Alive
- [x] Automatic HTTP Compression
- [x] Dynamic Serving
- [x] Modern Default Pages
- [x] Logging to Console
- [x] Basic HTTP Cache
- [ ] Password Protected Directories
- [ ] Custom Redirects
- [ ] PHP Support (Possible)
- [ ] File Indexing (Possible)

Note that more features are coming soon, and not all features in this list will be implemented.
