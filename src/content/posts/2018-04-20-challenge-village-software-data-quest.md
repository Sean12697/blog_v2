---
template: blog-post
title:  "Challenge - Village Software Data Quest"
date:   2018-04-20 20:00
slug: /challenge-village-software-data-quest
---

![Group Picture](https://villagesoftware.co.uk/media/1233/_dsc6146-2.jpg)

We were pointed towards the "[Village Data Quest](https://villagesoftware.co.uk/data-quest){:target="_blank"}" by [Matthew Crossley](https://twitter.com/MattyCrossley){:target="_blank"} through our student email and I was personally intrigued, especially with a description of what the challenge would entail (partly), that being the text given below:

> You and your team are competing against others in real time, to find the most valuable packages of land to claim.

> You are presented with a 1000 x 1000 csv grid, representing a type of natural resource found in the land. Each cell will have a value from 0 to 100 for each resource, each resource has a value.

> Your main objective is to find and claim 5 the most prosperous 10 x 10 pieces you can on the grid. Claiming a grid happens on a first come, first served basis. Once you have claimed a piece of land, no one else can claim any cells in it.

I asked [Iqrah Nadeem](https://twitter.com/i_iqrah){:target="_blank"} if she was interested in attending with me and she was.

## Pre-challenge

Given the challenge, I developed a solution for a given CSV file (which can be seen on [this](https://github.com/Sean12697/Village-Software-Data-Quest/tree/62250a5d495949c5d2049bb338b82d2513582b54){:target="_blank"} commit of my GitHub solution), which they recommended doing before the event to prevent issues loading CSV files on the day (since then we should be dedicating time to Data Science). 

I decided to use JavaScript since not only am I extremely familiar with it, and that it's not too optimise to perform such calculations, but if time let me I could also easily visualize what my solution is doing on a canvas (after console logging the needed results before render time overhead).

Essentially, the script I wrote passes over every possible 10x10 block, summing the values held within, then storing the position of that block (along with the total value) within an array.

I also generated test data within this script, which can be seen [here](https://github.com/Sean12697/Village-Software-Data-Quest/blob/62250a5d495949c5d2049bb338b82d2513582b54/script.js#L10){:target="_blank"}, which yielded correct results, although in early stages of development rich plots usually overlapped due to the resource locations being situated in certain locations.

To combat this, I had to develop a function which would run over the plots given and [getUniquePlots](https://github.com/Sean12697/Village-Software-Data-Quest/blob/62250a5d495949c5d2049bb338b82d2513582b54/script.js#L45){:target="_blank"}, this leading to a complete implementation of a fast algorithm (seconds to compute) for the information we were given.

Note: if you run this code you might run into a CORS issue, this is due to how I am loading the CSV file via a XMLHttpRequest, to solve this a plugin can be installed on most browsers to prevent this.

## The Day

After a brief introduction from Village we were given more information about the challenge, being briefly three more rules on top of what we knew:

- There would be four CSVs, one for each resource (Gold, Iron, Wheat and Oil).
- We had trade value of each resource from the past 6 months.
- We had to sell a resources from ALL claimed plots on a given month.

With these three new rules being introduced, it made developing a sufficient algorithm within the space of a few hours extremely challenging, giving time was a factor across resources (rather than just whole plots).

We decided that if we just take the current value of all given plots of land, then sell resources at their peak selling price, it would still produce extremely well yielding results (although not completely guaranteed the most prosperous).

To program in these new CSV files and find the most prosperous plots, we first used what I had produced before the new rules to iterate over the total (still a 1000x1000 piece of land), although this time not being directly from the CSV file.

I created a [recursive](https://github.com/Sean12697/Village-Software-Data-Quest/blob/5cef02a3f207dcd489d3b8a7963290629bde2421/script.js#L31){:target="_blank"} function which would pop a string for each file from an array, into another array holding the data from that file, then after it had finished the data would be passed to a new function that converted it from a string to a 2D array.

With each array I multiply them by their corresponding value (`for (var k = 0; k < arrays[i][j].length; k++) arrays[i][j][k] *= values[i];`), then sum every array together, from here it's then passed to the function I created prior to the event and logged.

## Submission

We were one of the first to submit our claims (only two claims being made by a group before us) and claiming our desired plots of land (using linier regression to decide the best time to sell each resource) and were confident.

Although half way through the hour we had to submit our plots, the organizer of the event (who produced the challenge) [Dominic Bisset](https://twitter.com/DominicBisset){:target="_blank"} asked us if we accidentally flipped x and y coordinates, due to a plot being revered yielded a far more prosperous piece of land and during testing he made the exact same mistake.

Digging into my code I found that on the following few lines that x correlated to the j variable in my loop, not i, losing us grand victory.

```javascript
    // finding the value of every possible plot
    for (var i = 0; i < arr[0].length - size; i++) {
        for (var j = 0; j < arr.length - size; j++) {
            jsonResults.push({
                total: sumOfSize(i, j),
                x: i,
                y: j
            });
        }
    } jsonResults = jsonResults.sort((a, b) => b.total - a.total); 
    // simple lambda function to sort
```

Lucky there was still the "Persuasion award", which I was confident we would win with my experience in presenting workshops and mentoring (teaching ideas/code/algorithms in understandable ways), and the fact Iqrah spend most of her time creating a smooth presentation for this element.

![Persuasion award](https://pbs.twimg.com/media/DbPbURVX0AACubA.jpg:large)

WE WON THE [PERSUASION AWARD](https://twitter.com/VillageSoftware/status/987374974397747200){:target="_blank"}, along with a Google Home Mini each, it was such a great a day and I do hope Village does run another Data Quest, they have also wrote up their [own blog post](https://villagesoftware.co.uk/blog/data-quest-round-up/){:target="_blank"} which is worth checking out for an overall round up of the event.