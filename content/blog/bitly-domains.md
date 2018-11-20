+++
author = "Moski Doski"
categories = ["bitly"]
date = 2014-07-22T13:36:54.804-07:00
description = "How many domains are using Bitly as a shortening service ?"
draft = false
image = "images/2014/07/bit.ly-logo.jpg"
slug = "bitly-domains"
tags = ["bitly"]
title = "How many domains are using Bitly as a shortening service ?"

+++

Last night while looking at my twitter stream, I noticed that you hardly see full URLs anymore. Most URLS are being shortened using the twitter URL shortener "t.co" or "bitly.com" or using some own custom domain shortener such as "tcrn.ch".

And that got me thinking, How many domains are using Bitly as a shortener service ? 

The short answer is a whopping _"19327"_ domains as of Jan/31/2012.


Started by looking at the Bitly api documentation but couldn't find anything useful. Google was not any better. Then i noticed how Bitly chrome extension expands all the shortened bitly URLs including the custom domain ones within a page. So they either download all the domains with the plugin (which is not very practical, because they need to update the plugin every time they add a new domain) or they have some hidden undocumented api call somewhere.

So, i opened the source code for the bitly chrome plugin which is located under `~/Library/Application Support/Google/Chrome/Default/Extensions/` if you are a mac user and started digging into the code.

After few grep commands, i found the following 2 definitions:

{{< gist moski 1713034 >}}

Which is really interesting. There is an undocumented API call to `/all_domains`. This function returns all the domains that are using Bitly as shortener service. As it turns out, they are actually returning the MD5 of these domains not the domain names. Which doesn't matter in our case because we only need to count them.

So i wrote a small ruby script to do the counting.

{{< gist moski 1713168 >}}



