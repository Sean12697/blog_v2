---
template: blog-post
title:  "[Hackathon #10] - Free Your Mind, with Code Nation and EMIS Health"
date:   2019-06-01 23:00
slug: /hackathon-10-free-your-mind
---

This is the first Hackathon I will be attending after becoming a co-founder of [Inevitable](https://twitter.com/weareinevitable){:target="_blank"}, meaning I was able to discuss and grow an idea before the day of the hackathon (which I rarely ever do).

## Initial Idea

My base idea was a platform to monitor a users social media feeds in order to predict patterns and do sentiment analysis, due to it being a one day hackathon, this seemed a reasonable project to design, even if I did end up in a team of one.

The idea grew more when [Ben](https://twitter.com/Ben_Grubert){:target="_blank"}, my co-founder, pointed out that one of the signs of suicide could be detected through the use of this platform, that being:

> <b>Sudden calmness:</b> Suddenly becoming calm after a period of depression or moodiness can be a sign that the person has made a decision to end his or her life.

As seen in a clinical article for [Recognizing Suicidal Behavior](https://my.clevelandclinic.org/health/articles/11352-recognizing-suicidal-behavior){:target="_blank"}.

A few other points that Ben made for me to work with are that there are two other good factors than can predict issues, the first being water usage, how much a person drinks and showers/baths, then the second electricity usage, indicating a persons circadian rhythm. Both of which if disrupted from a persons normal routine can be strong indicators of problems.

This drove my thinking of a platform which could be used by a carer to detect issues through leveraging only smart meters and social media, to have several stages to intervene on issues before they escalate.

The last discussion made before the day was a name for this platform, where Ben came up with the idea of "Caroline", being an abbreviation of "Carer Online".

## The Day

After a few pleasantries and pastries, it came to team building, there were many that came in teams and had assigned tables due to that, although the people like me that came were initially put into one large team of nine, which I tried to split up for managements sake (especially since I have personally not seen a team that big at any Hackathon before, maybe 7 or 8 at max).

Unfortunately, this is when the organisers decieded for us to do refine our ideas and let each one of us in the groups speak about our individual ideas, where we had near three and "this could be part of this" was said a lot by a few of the nine people on the table.

Due to this, I had to say that they could either come from one of two directions, either they wanted to use a particular piece of technology, like an Echo Dot, and find a solution to a problem from there, or they could home in on a specific issue/problem, and let a solution form.

After I said that and iterated my idea again, it left me with one other developer on my team, Kevin Thomas, who had recently been working with the Watson API for this Hackathon.

### Development

After finalising the team of two, we then split up task allocation, I was to initially form the front-end and make it look good, then Kevin was to build endpoints for me to call from my server, which would use the data I pull from Twitter for a given user, and run extra analysis on the text.

After a while, I both had a UI that I was happy with and I was also able to grab Twitter data from a quick Heroku server I whipped up (using NodeJS and the Twit package), from there it was nearing pizza time so I took a break for coffee before having some and continuing on.

As we were having coffee, we did discuss having the Watson chatbot intervene through Twitter DM's (or other social networked connected up to the platform) if it noticed "sudden calmness", since this situation could happen quite rapidly at night, where people are sleeping, and it would be useful to have some kind of mechanism in place to deal with late night issues.

#### Spot Prize

Just after pizza, as I started to look at the Swagger documentation Kevin had made for me further, a spot prize was announced, a prize given at a random time for particular reason.

As they announced it, they said about a certain persons pizza handling techniques, and doing a bit of research before the event, it was clear it was my team and we were given a pair of Raspberry Pi 3 Model B+.

### Last Hour of Development

After this we had one hour left, an hour I spent integrating the API Endpoints Kevin had made for me into the front-end using Jquery Ajax calls, which initially did not work due to an oversight of mine.

In the last 5-10 minutes I was able to get the data in a JSON format in time, but not in enough time for the demo, it was something and later on I were to format it the way I intended.

## Time

Our time was up for development and it was time to jump into the demos, there were several teams meaning it took a while and we nearly went overtime, but when it came to ours I had been too preoccupied with development to make a proper slideshow running through the specific use cases, business case and statistics (it was definitely not one of my good pitches).

Unfortunately... we did not rank (first, second or third), but it was fun especially getting a spot prize, I made the modifications to the front-end [demo](https://inevitable-team.github.io/caroline/) (the additional information from Kevin being formatted how I originally intended below), and made the same repo' public on [GitHub](https://github.com/inevitable-team/caroline/).

![Analysis](https://i.imgur.com/AGyGJ5O.jpg)