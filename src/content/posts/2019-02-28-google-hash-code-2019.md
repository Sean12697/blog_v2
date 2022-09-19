---
template: blog-post
title: Google Hash Code 2019
slug: /google-hash-code-2019
date: 2019-02-28 23:00
description: This years challenge was based on images and producing the most
  interesting slideshow, essentially we would be given files with theoretical
  images (horizontal and vertical) and we would have to pair slides based on the
  tags that the photos contained.
featuredImage: /assets/spxj1qcucvo069gz38me.webp
---

This years challenge was based on images and producing the most interesting slideshow, essentially we would be given files with theoretical images (horizontal and vertical) and we would have to pair slides based on the tags that the photos contained.

Example Input (4 referring to the amount of photos and 3/2 to the number of tags in that photo):

```
4
H 3 cat beach sun
V 2 selfie smile
V 2 garden selfie
H 2 garden cat
```

On a slide (giving the index of the photo wanted) could be either one horizontal photo, or two vertical ones, the tags being the ones in both photos for the two vertical photos case. 

```
3
1 2
3
0
```

The interest score would then be decided by the minimum of three criteria, those being the tags ONLY in the first slide, the tags SHARED amongst the two slides, then the tags ONLY in the second slide. With the interest score between every two slides being summed up you would then have the amount of points for that slideshow.

## Problem Solving

I did take part in Google Hash Code last year and my team got a score of zero since we spent too much time trying to code an elegant solution in Java, so to ensure we did not get 0 I came up with an idea and code to produce a valid output and try to optimise it slightly.

I choice NodeJS to code in, since I am very familiar with it and could easily produce a solution to fit the problem space, having only to use `let fs = require('fs')` to quickly prove I could get the data in and sanitize it quickly (below being what I wrote to do so).

```javascript
let obj = fs.readFileSync(`${fileName}.txt`, 'utf8').toString();
    photos = obj.split("\n").map(v => v.split(' '));
    photos = photos.slice(1, photos.length);
    photos = photos.map((v, i) => {
        v.i = i;
        return v;
    });
```

### Evaluating Slideshows

With confidence I decided to code the method they described they'd mark the output, choosing to go bottom up and produce a function which could take in a array of indexes and give me bag the tags for them. 

```javascript
function getTags(indexes) {
    let tags = [];
    indexes.forEach(i => {
        photos[i].forEach((v, i) => {
            if (i >= 2) tags.push(v);
        });
    });
    return tags.filter(onlyUnique);
}
```

After testing this function with console logs on various examples (`console.log(getTags([1, 2]))`) and verifying the output, I could then write a compare function for two slides that would be able to use the tags of photos given.

```javascript
function compare(a, b) {
    let a_tags = getTags(a),
        b_tags = getTags(b);
    let a_tot = onlyIn(a_tags, b_tags),
        union = unionCount(a_tags, b_tags),
        b_tot = onlyIn(b_tags, a_tags);
    return Math.min(a_tot, union, b_tot);
}
```

Similarly I tested this out with console logging (`console.log(compare([1, 2], [3]))`) but also writing a log within the function itself to verify the values (`console.log(a: ${a_tot} union: ${union} b: ${b_tot})`), which highlighted that initially within the onlyIn functions I was incorrectly passing `a` and not `a_tags`.

From there and around an hour in, I could then write the evaluation function needed to iterate over my potential slideshows, this was relatively easy since using an ES6 function and ensuring I don't go Out of Bounds (our team name).

```javascript
function eval(slideshow) {
    return slideshow.reduce((sum, val, i, arr) => {
        let t = (i != arr.length - 1) ? compare(val, arr[i + 1]) : 0;
        return sum + t;
    }, 0);
}
```

### Producing Slideshows

Still yet to submit a solution I decided to create a valid slideshow by splitting vertical photos and horizontal ones, paring each adjacent vertical photos and pushing them to an array, along with every horizontal photo. This in code looked like:

```javascript
function genSlides() {
    let V = photos.filter(v => v[0] == 'V'),
        H = photos.filter(v => v[0] == 'H'),
        slides = [];

    for (let i = 0; i < V.length; i += 2) {
        slides.push([V[i].i, V[i + 1].i]);
    }

    H.forEach(v => slides.push([v.i]));

    return slides;
}
```

With this I had an array that I needed to convert to the format they want, which wasn't difficult since all was required was the file system (fs) module from npm again and iterating over each value, which ended up as:

```javascript
function generateFile(slides, fileName) {
    var stream = fs.createWriteStream(`${fileName}_export.txt`);
    stream.once('open', function (fd) {
        stream.write(`${slides.length}\n`);
        slides.forEach(v => stream.write(`${v.reduce((t, v) => t += " " + v, "")}\n`));
        stream.end();
    });
}
```

With this I was able to wrap these up in a forEach function going over each filename, computing the slides and generating the results, which I've now added logged timings for every calculation of files.

```
5ms: a_example - 0
961ms: b_lovely_landscapes - 10
10ms: c_memorable_moments - 124
556ms: d_pet_pictures - 161691
1411ms: e_shiny_selfies - 101460
Score: 263285    Time: 2.95s
```

As you can see it only took under 3 seconds to generate output with scores not all being 0 (this is being ran afterwards so is not 100% accurate to when ran at Hash Code, it did score around 330,000), which were ready to submit and did initially give us a rank of 5 on the UoM leaderboard, but when I tweeted out someone had gotten a slightly better score than us (by a few hundred)

<blockquote class="twitter-tweet" data-dnt="true"><p lang="en" dir="ltr">I&#39;m competing in the <a href="https://twitter.com/hashtag/HashCode?src=hash&amp;ref_src=twsrc%5Etfw">#HashCode</a> Online Qualification Round and my team is currently in 6th place at United Kingdom / University of Manchester!</p>&mdash; 🧙‍♂️ Sean O&#39;Mahoney (@Sean12697) <a href="https://twitter.com/Sean12697/status/1101209599091376129?ref_src=twsrc%5Etfw">February 28, 2019</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

### Optimizing Attempts

The second thought I had was to scatter the arrays of slides an arbitrary amount of times and use the eval function I had created to get the best slides of closely paired vertical photos (which still needed improving).

For unknowns reasons it occasionally gave worse results (shown below) which I knew not to submit, but then did make me try and use a similar function on the pairing of vertical photos and permutations over the best randomly paired vertical photos, with the shuffled slides of those.

```
7ms: a_example - 1
35777ms: b_lovely_landscapes - 14
209ms: c_memorable_moments - 104
19915ms: d_pet_pictures - 147488
60242ms: e_shiny_selfies - 101358
Score: 248965    Time: 116.15s
```

Eventually one of my other team members found a more elegant solution in C# which did take longer (the last submission for file `e_shiny_selfies` was 4 minutes before the deadline), which I will review, but with that it pushed us up 4 places to #2 and settled our place there by a significant amount (being hundreds of thousands above everyone else, but still around 200,000 below the team at number one).

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Woohoo! My team, Out of Bounds, came in 2nd place overall in the <a href="https://twitter.com/hashtag/HashCode?src=hash&amp;ref_src=twsrc%5Etfw">#HashCode</a> Online Qualification Round at United Kingdom / University of Manchester. Our final score was 719912. 🏆</p>&mdash; 🧙‍♂️ Sean O&#39;Mahoney (@Sean12697) <a href="https://twitter.com/Sean12697/status/1101238831670534149?ref_src=twsrc%5Etfw">February 28, 2019</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

I am aware trying to pair vertical photos with more varying tags next to horizontal photos with many would have likely yielded greater results, although producing an algorithm in the few hours we had could have led us in the same predicament me and my team last year were in (not submitting anything in time).

I have pushed it to [GitHub](https://github.com/Sean12697/HashCode2019/) although did do so later on, meaning the iterations I did to try and shuffle the vertical photos are not there and now have added timings if you do want to run the script yourself (change [this](https://github.com/Sean12697/HashCode2019/blob/2d75560e9f6534f2123ae5ce5a276609f17417ea/script.js#L19) if you want to see the time difference between just generating slides, and trying to get the best).