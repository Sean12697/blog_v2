---
template: blog-post
title: "[Conference #3] - OggCamp 18"
slug: conference-3-oggcamp-18
date: 2018-08-18 22:00
description: Coming Soon
featuredImage: /assets/Dk31VPGXgAAT-y2.jpeg
---

I first found out about this un-conference only two days before it was to take place, from [May][may] who I met at BSides Manchester (my last Conference) two days prior, which came up in conversation since she was on Crew and was asking another friend of hers if they were attending.

Initially I was unsure if to attend or not, tickets were free, since the conference is about open source, although I would have to buy a return ticket to Sheffield and two if I wanted to attend both days (still being cheaper than finding a hotel/AirBnB).

It came to the night before the conference and I bought my train ticket, I was a little unsure what to expect especially since at that point the schedule was still being refined and only had it on the day, although I did see on their Twitter that they were accepting talk suggestions.

I had been working on one titled “Single Page Web App: Manchester Tech Meetups”, which would be a workshop that I would run for Web Students at my University (requested by my Course Leader) hopefully in the 2018-19 Academic Year, demonstrating thinking in an MVP (Minimum Viable Product) way and using RESTful API calls in JavaScript with DOM Manipulation, but I had yet to run it.

It came to the morning and I only had [three hours sleep][three-hours], but I got ready for my train to Manchester Piccadilly then from there Sheffield, working on my presentation on the near hour train up, unfortunately not on a table seat (which had all been reserved).

I had gotten a little lost being my first time in that part of Sheffield, but did arrive in time to connect to the Wi-Fi, see May, check the schedule and network slightly before the [Welcome Talk][welcome-talk]. It came down to three tracks I wanted to attend on Saturday, two before my track, the first being “Infrastructure as Cake”, but the second being my highlight, [“Fast, Free and Beautiful: Open Source Image Delivery Techniques”][talk-twitter].

## [Fast, Free and Beautiful: Open Source Image Delivery Techniques][talk-scedule]

This talk was by [Doug Sillars][doug], who I found out through Twitter knows [Harry Roberts][harry] (who I know from a Front-end Performance Masterclass I attended by him at The Shed) and a few similar points came across (along with other pieces of knowledge I knew beforehand), although Doug drilled more into specific optimisation techniques.

Starting off with statistics for why it is important to optimise images, how it increases load time and therefore loses users, losing 1% revenue for a 100ms difference in load time for Walmart & Amazon in 2001.

One of the first methods to combat this was compression, where usually a setting of 85 is optimum, between compression of an image and its quality, then directly following that the formats specifically, for images webp (by Google) is one of the most optimised and getting more support by browsers.

A few of the next methods I was very familiar with, although when it got to Lazy Loading I had only heard and seen it implemented, never thinking of every to implement it, essentially only loading images that are in view of the user initially, saving loading time for those over the fold (having placeholder images there until the user scrolls to them). This technique currently requires Web Developers to implement one of the JavaScript solutions out there, although Doug did mention it is being tested to be built in natively.

The next unknown method to me was [Responsive Breakpoints][responsive-breakpoints], essentially loading different images for different screen sizes, rather than just the one that would display on both mobile and desktop, which would be the same size, although many of the pixels would not be used when rendered on a mobile device, essentially downloading un-needed data and rendering time.

Last of all there is a website/service called [Cloudinary][cloudinary], which is “the image back-end for web and mobile developers. An end-to-end solution for all your image-related needs.”

## [Single Page Web App][talk]

After all of this it shortly came time for my talk, making sure my slides were fine, laptop was charged and a little bit of networking (with [Tanya][tanya]) before heading up to the sixth floor where my room was.

I had a rough audience of 15, which for a last minute scheduled talk was not a bad turn out, unfortunately during the trip in the elevator the Wi-Fi cut out on my laptop, so during my demo API calls broke and I needed to log back in, I decided to skip the live demo since I only had 25 minutes to present my talk with questions.

Out of my over 15 previous presentations I would say that was one of my worse in terms of smoothness, although I got good feedback and it was quiet useful for a few people, especially a few there were getting into Web’ Development.

## Socialising 

After this track it was lunch, so most went out to various places to grab a bite to eat and after this period I spent the rest of my day networking and talking about web stuff, quite repetitive and calmed down for the night.

After the conference I spent the rest of the night with May and a few friends of hers, having a laugh, talking about security and ending up in [Gourmet Burger Kitchen][gbk] before I had to catch my last train at 22:11.

[may]: https://twitter.com/SleepyEntropy
[doug]: https://twitter.com/dougsillars
[harry]: https://twitter.com/csswizardry
[tanya]: https://twitter.com/tanurai
[three-hours]: https://twitter.com/Sean12697/status/1030698943867432961
[welcome-talk]: https://twitter.com/Sean12697/status/1030749644131844096
[talk-twitter]: https://twitter.com/Sean12697/status/1030765339230064647
[talk-scedule]: https://joind.in/event/oggcamp-18-2018/fast-free-and-beautiful-open-source-image-delivery-techniques
[responsive-breakpoints]: http://www.responsivebreakpoints.com/
[cloudinary]: https://cloudinary.com/
[talk]: https://joind.in/event/oggcamp-18-2018/single-page-web-app
[gbk]: https://twitter.com/Sean12697/status/1030908159718776832