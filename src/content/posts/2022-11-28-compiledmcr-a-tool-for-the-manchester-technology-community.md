---
template: blog-post
title: "CompiledMCR: A Tool for the Manchester Technology Community"
slug: compiledmcr-a-tool-for-the-manchester-technology-community
date: 2022-11-26 20:58
description: In this blog post, I'll talk about the goals of CompiledMCR, an
  open-source project started in 2017 inspired by TechNW to help the whole
  technology community within Manchester.
featuredImage: /assets/manchester.jpg
---
In this blog post, I'll talk about the goals of [CompiledMCR](https://compiledmcr.com/), an open-source project started in 2017 inspired by [TechNW](https://technw.uk/about.html) to help the whole technology community within Manchester.

## CompiledMCR Origins

Beginning with Git commit [b2daed0](https://github.com/Sean12697/MeetupManchesterTech/commit/b2daed089e7f38f3805c4fa82054bcdce3bd8ae9), the first solution addressed by the platform was overcoming the pain of trying to search for other groups on the Meetup platform. It became a common occurrence, after attending nearly 100 events at the time, that similar groups were hidden via the built-in Meetup search function and were primarily shared by word of mouth. 

A great example of this was the [React Meetup group](https://twitter.com/mancreact), which commonly met in MadLab, and attendees occasionally said to other attendees, "I'm interested in learning about Angular as well; if only there was a Meetup group for that," to which I used to reply, "Actually, there is one, and it meets here monthly as well; open up Meetup...," and then the rest was history.

This commit only pulled data from the Meetup API at the time, which is now deprecated, although it fulfilled the goals at the time and did not require the manual entering of events, which the TechNW calendar did; instead, only groups were required to be entered and the rest was automated; not too bad for a night's work by a second-year Computer Science student at the time.

From there, its features and goals met both the maker's and the Manchester Technology Community. It's local knowledge that Meetup comprises the majority of technology networking events, generally, although both the TechNW calendar and Eventbrite hold the details for many more. 

This is why, over time, these were implemented to serve the needs of event exploration, and then further, a [dynamic ical file](https://twitter.com/Sean12697/status/1133340835054018560) was produced to integrate directly into users' calendars to enable an easier oversight of both the technology events happening and the availability of the individual.

## The Future

Aside from the features that have already been implemented, there is a desire to greatly assist community organizers. As one myself and as someone who has helped many others over the years, most of my decisions and suggestions have been data-driven, and a lot of them can be backed up and proven by historical data that can be accessed through the APIs of platforms like Meetup.

### An Example of Data-Driven Decisions for a Hypothetical New Group

What venues are popular and what events to avoid clashing with are excellent examples of data-driven decisions that can be explained. For example, if you're trying to start a new community group, no matter what platform you're going to use (Meetup, Eventbrite, etc.), extracting local knowledge from existing platforms' raw data can help a lot with its success.

If a new AI or data group wanted to start, it would be useful to know about groups such as [Open Data Manchester](https://www.opendatamanchester.org.uk/), [PyDataMCR](https://twitter.com/pydatamcr), [MancML](https://mancml.notion.site/), [Her+Data MCR](https://twitter.com/herplusdatamcr), and other such related groups, even if they do not contain the keywords within their names, such as [R Ladies MCR](https://twitter.com/rladiesmcr) and [Python North West](https://pynw.org/). With this knowledge, you know that it's most likely not preferable to organise an event on the same night as theirs, unless you plan to collaborate with them.

Further to that, once you try to organise an event on a given night and none of these groups are hosting one and you find a suitable night to host one that coincides with the preferred decisions of the scene, which is a whole data-driven process in itself, you then need a venue. 

Fortunately, that data is also available on platforms such as Meetup, indicating that venues such as AutoTrader are not only popular, but have also been used by other community groups following the pandemic, whereas others, such as [Federation House, have not](https://twitter.com/WeAreInevitable/status/1340959753560870912).

### Difficult to Explain Decisions

Unfortunately, some of the pieces of common knowledge shared amongst community organisers over the years are difficult to explain, owing to the fact that some of the required data was not originally recorded or is not easily accessible.

A great example is attendance ratios, where the best you commonly get is people who have RSVPed, which is not the same as attendance, with generally 2/3 of RSVPs translating to attendance for free events in the City Center pre-pandemic with standard weather conditions. Knowing this frequently and influencing factors changes, for example, the quantity of refreshments to order for catered events as well as the costs of sponsorship.

## Contributing

As stated at the beginning of this blog post, this project is open source, primarily focusing on [events](https://events.compiledmcr.com/) ([Github Repo](https://github.com/inevitable-team/compiled-mcr-events)) with a current analytical [data](https://data.compiledmcr.com/) element ([Github Repo](https://github.com/inevitable-team/mcr-tech-meetup-data)). 

We have big plans to revamp and vastly improve the platform while staying true to its roots as a tool to help the Manchester Technology Community rather than being just a sales tool for us. 

Feel free to reach out, and for now, please use it as it is to find likeminded people to collaborate and innovate with.

Logging off!