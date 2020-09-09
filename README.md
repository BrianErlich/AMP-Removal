# AMP-Removal
A Javacord discord bot that replaces AMP links with the source article link.

Utilizes Jsoup for html parsing, and a big shoutout to [this comment from umezo on Stack Overflow](https://stackoverflow.com/a/56170002/14102200), it showed me the basics of html parsing.

# What are AMP links, and why are they bad?
Accelerated Mobile Pages is a Google program, designed for people with bad internet. It caches the important parts of an article's web page, and then displays to to the user.
The issue is that these cached pages are stored on google's servers, and when you visit an AMP site, you're seeing ads from google. The publisher gets little to no money from this.
Sources [1](https://www.reddit.com/r/explainlikeimfive/comments/ecrzvp/eli5_what_are_amp_pages_and_whats_bad_about_them/fbdfymd?utm_source=share&utm_medium=web2x&context=3), [2](https://medium.com/@danbuben/why-amp-is-bad-for-your-site-and-for-the-web-e4d060a4ff31), [3](https://en.wikipedia.org/wiki/Accelerated_Mobile_Pages#Reception)

# Getting rid of AMP links elsewhere
I am not associated with the developer of these, just found them while browsing.
* Firefox
  * [Link to Firefox addon](https://addons.mozilla.org/en-GB/firefox/addon/amp2html/)
* Chrome
  * [Link to Chrome extension](https://chrome.google.com/webstore/detail/redirect-amp-to-html/kifkmmpiicbcnkjaliilaoeaojlldonl)

I am not associated with the developer of those, just found them while browsing.

# How the bot works
When an AMP link is sent in a channel (https://www.google.com/amp/s/), it does the following, in order:
1. Establishes a connection to the source page
1. Using, [Jsoup](https://jsoup.org/) and [OgMapper](https://github.com/iumehara/ogmapper), attemps to grab the metadata of the article, using
   1. OpenGraph tags
   1. Plain meta tags
   1. Twitter tags
1. Makes an embed with 
   * The icon & name of the user who sent the link, linking to this readme
   * The title of the article, linking to the source
   * The article description
   * The article thumbnail
1. Deletes the original link sent with reason `"Amp Link."`

# Example
