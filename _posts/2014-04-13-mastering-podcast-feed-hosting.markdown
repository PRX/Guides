---
layout: post
title:  "Mastering Podcast Feed Hosting"
date:   2014-04-12 18:22:03
categories: podcasts
---

The technology behind podcasts is pretty simple. Every podcast has a specially formated file, called an RSS feed, that is publicly available on the internet which lists all of the show's episodes. iTunes, Stitcher, and other podcast websites and applications check the RSS feeds periodically to see if any new episodes have been released.

The RSS format was not specifically created for podcasts, but because of the way it was designed it works quite well in that role. There are many things to consider when publishing an RSS feed for a podcast. Often times podcasters make mistakes when creating their feeds, but don't know why things aren't working correctly.

## Hosting

Even if you aren't a web developer or don't have much experience with web hosting, there are few very important things you should be aware of to ensure your podcast feed functions properly.

### MIME Type

Similar to how files on your own computer use `.mp3`, `.gif`, or `.pdf` to describe what kind of file they are, files on the internet also identify their type. Files on the internet use a more formal method, which is called a **MIME type**, and looks like `image/gif` or `application/pdf`.

The MIME type used for podcast RSS feeds is often set incorrectly. Because RSS files are a type of XML file, sometimes feeds will use the MIME type for XML. Other times the MIME type identifies the feed as a plain text file, because it can be opened with a text editor.

The actual MIME type that should be used for all podcast RSS feeds is `application/rss+xml`. Some software is designed such that it only recognizes files that use this correct MIME type, and will ignore any other file type. If your feed, for example, were incorrectly identified as `text/plain`, some podcast apps may consider it invalid and fail to subscribe to it or find new episodes.

If you are unfamiliar with how to check the current MIME type of your feed, or make changes if it's not correct, you should contact your hosting company.

### ETags

Every time a request is made for your podcast feed (like from a browser, podcast app, or iTunes), the server hosting the file will send bits of additional data along with the file itself. This additional data is called metadata, and provides extra information about the requested file, such as it's age, if it's been compressed, and its size.

One piece of metadata that can be included is called an **ETag**. ETags are often nonsense values like `e20b80361b754ef9a1b07fbd0ec2363c`, which don't mean a lot to a person, but can be very useful for computers and applications. The actual value of the ETag is not important, nor is where the value comes from or how it's generated.

The purpose of an ETag is to help determine if a file has changed since the last time it was used. In the case of a podcast feed, for example, a new episode may only come out once a week. That means the RSS file is only being updated once a week, but a listener's podcast app on their phone may be checking for new episodes much more often, sometimes even several times an hour.

Without some way of knowing if the feed has changed, the podcast app would need to download the entire feed every time it checks for updates. For podcasts with hundreds of episodes that can mean doing a lot of extra work for nothing, slowing the app down and creating a bad experience for the user.

Well-designed podcast apps will make a record of each feed's ETag every time there's a change. On subsequent updates, rather than just asking for the entire feed file no matter what, the app will send the web server the ETag it previously made a record of. Properly configured web servers will check to see if the ETag that was sent by the app matches the current version of the feed. If there is a match, rather than send back the entire, potentially large, RSS file, the server will send back a small message telling the app that the feed has not changed yet.

This can reduce the time needed to check for and process new episodes of a single podcast from one or two seconds down to a tenth of a second or less. ETags are only helpful, though, when all the parts of the system work together properly.

The ETag's value must change whenever the feed gets updated, or an app could miss a new episode. But the value must also *only* change when the feed gets updated. Some web servers incorrectly generate a new ETag value every time a file is requested. This is functionally the same as having no ETag, since the value on the server and the value in the listener's podcast app would never match.

The web server must also correctly identify those matches, and send back the message to indicate no changes have been made, rather than just sending back the whole file.

If you are unfamiliar with how to verify that ETags are working properly, you should contact your hosting company.

### Encoding

Computers have many different ways of defining how text files work. Some text files only support basic characters like english letters and numbers. Others can include additional characters like â or é, or even a snowman ☃.

Podcast feeds are intended to support an extremely wide array of characters. They use a format called `UTF-8` to do this, which is a system for encoding text files that nearly every computer and device now supports.

In order to ensure that everything using your podcast feed knows that it is UTF-8, there are two things you should do.

First, inside your RSS file, there's a way of telling anyone reading the file (including software) which format you're using. Generally it will look something like this:

    <?xml version="1.0" encoding="UTF-8"?>

This line includes information besides the text encoding, but `encoding="UTF-8"` is the part declares the file as UTF-8 and it should be present in every podcast feed.

The other place where file encoding can be set is in the metadata, like where the ETag information was found. Text encoding is included in a metadata value called `Content-Type`. If you are unsure how to determine if the web server is properly identifying your feed as UTF-8, you should contact your hosting provider.

Proper text encoding is imporant because software reading your podcast feed, like iTunes or a podcast app, will use one of these two values to determine how to interperet the data in the file. If one of the values incorrectly identifies the feed as something other than UTF-8, the app may read the file improperly. This will result in letters and symbols being displayed incorrectly or unreadable.

### Domain Names

Where your podcast feed is hosted is largely a matter of preference and necessity. Some podcasters prefer to use Wordpress, Libsyn, Feedburner, static files, other services, or some combination of those options. As long as the choice you make allows your feed to properly support text encoding, ETags, and MIME types, it mostly doesn't matter.

Your hosting decisions become more important when they impact the domain name and URL for where your podcast feed lives on the internet. It's very important to make choices as early as possible that will ensure issues related to your feed's URL don't hurt you down the road.

The main issue that you want to avoid is the URL of your podcast feed changing. This would cause your listeners to stop getting new episodes, and require everyone to resubscribe to your show. In some cases this could also mean that your podcast would show up twice in aggregators or podcast directories, and people may continue to subscribe to a feed that isn't being updated.

Many times changes to podcast feed URLs are not made by choice. Third-party services, even those run by large, well established companies, may shut down eventually. If the only URL for your podcast is provided by a service that shuts down, you will have no choice but to find a new home for your podcast and hope listeners move with it. If the change happens suddenly, you may not even have the opportunity to alert your listeners to the change.

By far the easiest way to protect against that is by having complete control over a domain name where your podcast can live indefinitely. Domain names cost as little as $10 a year, so even for podcasts with minimal budgets, it's a worthwhile expense to ensure the listeners you gain over time won't suddenly get lost someday.

Using your own domain does **not** prevent you from using popular services like Libsyn or Feedburner, and doesn't require that you provide your own web server or hosting.

If you are starting a new podcast you should register a domain specifically for the show, and establish a URL at that domain where the show's feed will live. That is the only URL you should use when submitting the feed to places like iTunes, Stitcher or other aggregators, even if you are using a service like Feedburner, and also have a feedbuner.com URL for the show. Services like Feedburner have instructions on how to configure the settings to support your own domain name.

If you have an existing podcast but haven't been using a single URL that's completely under your control for the feed, the transition can be harder. If, for example, the feed URL that you have been using is a Feedburner URL, there are a number of steps you should take.

First, after you have set up your domain name and your feed is available at the new URL, you should add the `itunes:new-feed-url` tag to the old feed with the new URL. This will tell the iTunes Store to update its record of where to check for your podcast feed. Other apps or aggregators may also use this value to update their records, but there is no guarantee of that, so you should keep an up-to-date feed available at the old URL for as long as possible.

Except in the case of iTunes, because there's no guaranteed way of moving a podcast, the best way to ensure you don't lose listeners unnecessarily is by making an announcement on the podcast itself. Tell the listeners where to go to subscribe to the new feed, and where to find more information about the change. Because Android devices and third-party iPhone podcast apps are becoming popular, it's important that you take into account the needs of people outside of the iTunes ecosystem.
