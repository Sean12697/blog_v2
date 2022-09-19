---
template: blog-post
title: Hack Jam - Storytellers United
slug: /hack-jam-storytellers-united
date: 2019-02-28 20:00
description: Coming Soon
featuredImage: https://pbs.twimg.com/media/D0gk_dEW0AA8RwH.jpg:large
---

This event was emailed to us through our student email by Peter McKenna, it was promoted as a "BBC Digital Cities Hackathon" with the following content:

> We will be hosting a two day hackathon in the Shed as part of the BBC Digital Cities programme. The event runs from 27th to 28th February, and offers valuable hands-on experience of object based media production, including the use of video and HTML5/WebGL media processing JavaScript libraries such as videocontext.js and seriously.js.

Being more of a creative hackathon I was eager to attend, although the only tickets that were available were "Expression of interest", meaning we would apply to attend and receive an email at some point in time to tell us we were confirmed.

Since I'm writing up this blog post, I was lucky, along with approximately 60 others, receiving an email from EventBrite with the following sentence:

> Storytellers United, BBC R&D, University of York are very happy to announce you have been selected to take part in the Storytellers United Hackjam event from 27th - 28th Feb.

After this email we received another a few days later with the schedule, recommendations and the Slack channel link. 

## Day One

After arriving at the Shed early at 9AM and waiting for others to arrive, [Philo](https://twitter.com/phivk) welcomed us to Storytellers United and made us join together in a circle and introduce ourselves, but with a twist of "If you were an emoji, which emoji would you be", obviously me being 🧙 (a Wizard, Web Wizard).

Once a few talks were done we were split up into our allocated teams, which were created prior to the event to balance out the skills in each team, although unfortunately, a few did not attend leaving some teams lacking certain skill sets.

But particularly in my team, comprising of Marsha Courneya and Donna Wood, both writers that have done small parts of video and editing work before, we seems pretty balanced and set to start coming up with ideas that we could develop.

### Ideas

Initially we discussed the idea of surveillance and how data reigns us, how dystopian the future could be but how data sometimes is not put in context (defining us as data but not properly).

Donna put the example forth of how she researches a lot of politically right wing websites, for journalism research, but how that to advertisers could make them think she is politically right winged, even though that could not be the case (since the searches aren't in context).

From there we had a few rough ideas of how to use this to tell a story, how a users data would be used to produce one, including various ideas of slot machines, crystal balls and deities.

#### Workshops

After a short time to get familiar with our team members and start generating ideas, we were introduced to a few tools by people who work on them and we could use to help produce our ideas.

The two of interest for me particularly were [videocontext.js](https://github.com/bbc/VideoContext), a JavaScript library to sequence and apply effects on videos easily in a canvas, and [Cutting Room](https://github.com/Object-Based-media/cutting-room), a visual interface that uses the Video Context library.

I ended up attending the Cutting Room workshop presented by [Davy Smith](https://twitter.com/DDDDavy) since I could read the videocontext.js documentation on GitHub and hopefully use it without much difficulty (if I needed/wanted to).

Once this was finished it was a small lunch break then back to our teams to keep refining our ideas and hopefully come up with a more concrete idea of what we would produce and demo.

### Idea Refinement / Development

Eventually we went with the idea of the "Data God" as a figure to narrate our story, but from there what data would the Data God use, how would it form the story and from a technical aspect how would it work.

YouTube videos were picked as our data source after a slight discussion, I did suggest Twitter since I knew the API was easy, although [Jonathan Hook](https://twitter.com/jonathanhook) helped me find a way of interacting with the YouTube API without having to get OAuth tokens and so on.

With this I started writing code that would be used to interact with YouTube, hopefully being easy to implement into Cutting Room which Marsha was working with (along with Donna and our new team member Robin Moore from the BBC producing the video content, Donna the audio and Robin the GCI).

Liaising with my team I continued development and getting useful aspects of the video we could use as data and how to respond to that, initially we thought of ways that the tags on the video could determine the outcome, although without doing NLP it would be quite difficult in the time we had.

After a bit more discussion, we decided that the "Data God" would ask for a video that made the user feel good, one that they didn't like, then a guilty pleasure one, which would be responded to. To deal with this, we thought broad catagories would be good, them being music, food and animal videos (implemented for them demo), which would have generic responses like "that music hurts my ears".

Development wise it took long than it should have for me to realise there was a category id property I received back for a given video id, being a numeric string which I found a mapping for online.

At this point it was getting close to dinner and when given the website I was working on food videos to get a relevant category, there was never one specifically for food, meaning I had to implement one.

After dinner (being around 40 pizzas for about the same amount of attendees), I wrote the following function to get a category including food before calling it a night for day 2.

```javascript
function getCategory(video) {
    let foodBool = video.items[0].snippet.tags.reduce((sum, curr) => sum || curr.toLowerCase().includes("food"), false);
    return (foodBool) ? "Food" : categories[parseInt(video.items[0].snippet.categoryId)];
}
```

## Day 2

Arriving at the Shed again at 9AM, it was 3 hours until the deadline meaning the pressure was on. We all had ideas over night and one that we implemented was that the "Data God" should suggest to you a video, meaning if you gave it a food video, it might suggest to you an exercise video to watch instead.

Development wise this was not too difficult, I created another array/object of suggested video for each category, then with the following function it would return back a video ID that could be used by the functions I had previously wrote.

```javascript
function getSuggestedId(category, type) {
    let reverseType = (type == "Good") ? "Bad" : "Good",
        suggestedCategoryExists = suggested.hasOwnProperty(category),
        array = (suggestedCategoryExists) ? suggested[category][reverseType] : random[reverseType],
        video = array[Math.floor(Math.random() * array.length)];
    return (video == "") ? "NpEaa2P7qZI" : video;
}
```

This is not too important to understand, although because I did not fully populate the arrays, if it did get a blank string/ID, I would instead use a placeholder video.

From there it was time to put together my script and what Marsha was working on in Cutting Room, whiles Robin and Donna produced an example video which would be used in the demo if we would not make it work in time. Discussing with Davy slightly it seemed as converting my code into a class (being put on a new [branch](https://github.com/Sean12697/YouTube_Video_Info/tree/class)), since it could be initiated in Cutting Room easier, although after spending approximately half an hour on it, I was having issues with async functions not being detected within the class.

Whiles working on the class I was essentially rubber duck debugging with [Alexa Steinbrück](https://twitter.com/alexabruck), as she mapped out the general interactions from the users perspective, which Davy came over and looked at. Unfortunately it seemed as he understood our approach incorrectly initially, having suggested that Cutting Room was appropriate for us, in which it wasn't and it would be easier for me to code it (which we had the option of initially but did not go with to spread work amongst the team).

This left me with an hour to try to get interactions with video to work with the flow and interactions from the user (put on a [new branch](https://github.com/Sean12697/YouTube_Video_Info/tree/classic)). Theoretically what I produced in that time would do the first half of the demo, relaying the "Demo God" response to a music, food or animal video, although did not work in time.

### Demo

Luckily Robin had produced a finished [example interaction video](https://www.youtube.com/watch?v=aaTm0bS6264) with Donna which would be played at the beginning of our presentation, then I demoed what I had finished for the [website](https://sean12697.github.io/YouTube_Video_Info/) in the morning being that you could give the "Demo God" a video ID, it would receive the correct video and category, then suggest to you an alterative video you should watch.

We went first with this then the other teams demoed (which can be seen on [Hack Dash](https://hackdash.org/dashboards/suhackjam)), they were all very interesting their own regards, but once we had all finished we voted for which we thought was best over the three areas.

Our team ended up winning for "Most Original Concept" and do hope to work on it more and together, along with keeping in touch with everyone else especially the amazing organisers and mentors.

![Most Original Concept Photo](https://pbs.twimg.com/media/D0gk_dEW0AA8RwH.jpg:large)