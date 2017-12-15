---
layout: post
title: Serve Jekyll on Wifi
date: 2017-12-15
categories: 
authors: nichol
tags: 
blurb: So you want to serve your very important blog to other users of your wifi?  Gotcha.
---

Localhost.  It's local and it's a host but what good does that do you when you want to check in on your locally runnying jekyll blog that only you read from your bed on your phone?

Easy peasy.

```ruby
jekyll serve --host 0.0.0.0
```

Then run up `ifconfig` (assuming you're mac-ing) and look for the `inet` on your `en0` interface.  That's your IP on your network.  On mine, it's 10.0.1.95 and this is what it looks like:

![ifconfig.png]({{ "/assets/serve_jekyll_on_wifi/ifconfig_screenshot.png" | absolute_url }})


Now make sure your phone is on the same wifi network, hit up http://10.0.1.95:4000 from your phone and... oh yeah.  Your sweet sweet blog.  Just for you.  From your computer via wifi to your phone.  Pretty soon you're gonna be your own ISP, amirite?

Yes, but why?  Jekyll or Rails or most servers run locally default to only listening for traffic on localhost, which only comes from... local... host?  So if you want that webrick listening on your actual ethernet channel for connections, set it to 0.0.0.0 and that does the trick!

