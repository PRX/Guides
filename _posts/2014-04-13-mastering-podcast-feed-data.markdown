---
layout: post
title:  "Mastering Podcast Feed Data"
date:   2014-04-12 19:22:03
categories: podcasts
---

A majority of the interaction listeners have with a podcast is not with the audio or video you produce, but with the data in the podcast feed.

When searching through the iTunes Store or deciding what to listen to next in the app on their phone, listeners are greatly influenced by the data you provide in your podcast feed. A catchy title may entice someone to subscribe to your show, and a bad episode name may mean someone doesn't realize their favorite comedian is in the new epiode and they skip it.

There is a lot of data that goes into a well produced podcast feed, but once you understand how it all works and why it's valuable [[something will happen]]. Mastering the data in a podcast feed involved both technical and editorial aspects, but...

## Basic Structure

A podcast feed is actually a specialized type of RSS feed. While RSS is a well-defined specification for using XML to structure some content, using RSS for podcast feeds is not so well-defined.

Over time a number of practices have been adopted by the podcasting community, which expand upon the core of RSS to support the various needs specific to podcasts.

XML, the technology behind the RSS standard, allows a file to list out which additional standards it is utilizing. Most modern podcast feeds incorporate a number of standards:

    <rss
      xmlns:content="http://purl.org/rss/1.0/modules/content/"
      xmlns:itunes="http://www.itunes.com/dtds/podcast-1.0.dtd"
      xmlns:media="http://search.yahoo.com/mrss/"
      xmlns:sy="http://purl.org/rss/1.0/modules/syndication/"
      xmlns:dc="http://purl.org/dc/elements/1.1/"
      xmlns:atom="http://www.w3.org/2005/Atom"
      version="2.0">

Including these declarations will ensure that even software that strictly enforces files having valid XML will work properly with your feed.

Every RSS feed must include a `<channel>` tag, and for podcast feeds this represents the main container for all the data about your podcast.

For a podcast feed there are a number of tags that should always appear directly inside the `<channel>` tag.

##### Link

Link is a URL for the podcasts's webpage (i.e. not the URL for the feed). The link tag is required, and should never be blank. You should always have at least a very basic webpage with information about your podcast.

    <link>http://mygreatpodcast.fm</link>

##### Title

This is the title of your podcast, as it will appear aggregators, directories, and applications. It should **never** include any HTML or other formatting.

    <title>My Great Podcast</title>

##### Description

A simple and short phrase or sentence describing the podcast. This should **not** be a lengthy summary of hosts, guests, producers, topics, etc. It also should **never** include any HTML or other formatting.

    <description>A podcast by me that's great!</description>

##### Language

The primary language that your podcast is produced in. The value for this tag must be one listed here http://cyber.law.harvard.edu/rss/languages.html. The value should always be lowercase.

    <language>en-us</language>

##### Copyright

A basic copyright notice for your show. If you release the podcast under a Creative Commons license or something similar, list that here as well.

    <copyright>Copyright © 2014 My Great Podcast. All rights reserved.</copyright>

##### Editor

The editor is the person primarily responsible for the show's content. This tag must include an email address, and can optionally include name or title following the email address in parenthasis.

    <managingEditor>editor@podcast.com (Jane Doe)</managingEditor>

##### Technical Contact

A technical contact should be listed in case someone has an issue with the show's feed or the audio or video files for the show's episodes. This tag uses the same format as the **Editor** tag.

    <webMaster>help@podcast.com (Alice Doe)</webMaster>

##### Publication Date

The **publication date** listed in the feed's `<channel>` tag should be the last time show content listed in the feed was changed. There are times when the feed data itself may change (for instance, the person listed as the technical contact may be updated) even though no show content changed; those changes should not impact the publication date.. The format this tag's value should always match the following example, including being listed in the UTC/GMT timezone, and using `Z` to indicate that.

    <pubDate>Tue, 01 Jan 2013 03:30:00 Z</pubDate>

##### Feed Build Date

The **build date** for the feed should be updated any time the feed changes, including changes not related to the show's content. This tag uses the same format as the **publication date** tag.

    <lastBuildDate>Tue, 01 Jan 2013 16:51:59 Z</lastBuildDate>

##### Categories

The category tag is used to help classify the feed's show. These should be general categories that apply to the show as a whole, and make sense for most, if not all, individual episodes. Multiple categories can be listed for a single show, and you can use any categories you would like; there is no list to choose from.

    <category>News</category>
    <category>Technology</category>

##### Image

Listing an image for your show can improve the appearance of the podcast in apps and directories. The `<image>` tag include several other tags which hold actual values. The `<url>` tag points to GIF, PNG, or JPEG file representing your podcast. The `<title>` tag describes the image, and the `<link>` tag should be the same URL listed in the `<link>` tag for the podcast itself. `<width>` and `<height>` are limited to 144 and 400 pixels, respectively, and you should always include the actual values for the image you are using. The `<description>` tag is used to describe the link, in cases where the image is itself a link to the web page.

    <image>
      <url>http://mygreatpodcast.fm/logo.png</url>
      <title>My Great Podcast square logo</title>
      <link>http://mygreatpodcast.fm</link>
      <width>100</width>
      <height>100</height>
      <description>Check out the home page for the My Great Podcast podcast.</description>
    </image>

##### Documentation

By convention, all RSS feeds, including podcast feeds, should link to the document describing the RSS file specification. This should always be the following value:

    <docs>http://blogs.law.harvard.edu/tech/rss</docs>

##### Atom Support

While Atom and RSS are seperate formats for structuring data, podcast RSS feeds should include an `atom:link` tag for maximum compatibility. The `href` value for this tag should be the primary, canonical URL for the feed itself.

    <atom:link href="http://mygreatpodcast.fm/podcast.xml" rel="self" type="application/rss+xml" />

