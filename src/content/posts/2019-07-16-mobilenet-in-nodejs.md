---
template: blog-post
title:  "Development - MobileNet in NodeJS (Backend)"
date:   2019-07-15 20:00
slug: /mobilenet-in-nodejs
description: Coming Soon
---

The origin of this blog post started when I wanted to be able to classify images on a backend server as a learning exercise, to able to expand upon it for a project we are working on at my company (using a general object classifier as a baseline), and to also use computational power which will be needed further on. 

Primarily as a NodeJS developer, I wished to complete the task in Node, knowing that TensorFlow.js had models which I could use, and that MobileNet was the most broad (being able to classify hundreds of objects, which I learned whiles using it for my Mobile Application Development Unit in University).

Going through tensorflow on Github I found their [tfjs-models
](https://github.com/tensorflow/tfjs-models){:target="_blank"}, a list of trained models where [MobileNet](https://github.com/tensorflow/tfjs-models/tree/master/mobilenet){:target="_blank"} was listed and where I started reading the documentation.

In the readme it had a section for Usage "via NPM" (shown below), which I thought implied on the backend, especially since "via Script Tag" has usage documentation (definitely for the front-end).

```javascript
// Note: you do not need to import @tensorflow/tfjs here.

import * as mobilenet from '@tensorflow-models/mobilenet';

const img = document.getElementById('img');

// Load the model.
const model = await mobilenet.load();

// Classify the image.
const predictions = await model.classify(img);

console.log('Predictions: ');
console.log(predictions);
```

The first thing that seemed odd was the use of `document.getElementById('img')`, which is a front-end concept (the document being the webpage you are on), which lead me to try to find if anyone else has tried this task before.

Fortunately for me, a developer called James Thomas wrote a blog post back in 2018 called [Machine Learning in Node.js With TensorFlow.js](http://jamesthom.as/blog/2018/08/07/machine-learning-in-node-dot-js-with-tensorflow-dot-js/){:target="_blank"}, which gave useful advice, explained why elements would not work in NodeJS (as I found prior to attempting to run the demo code), how to fix these issues and gave code snippets (which I started experimenting with).

After trying to run their code, I found that it did not even get past `npm install`, combing through the console logs I found that TensorFlow.js was trying to be complied through [node-gyp](https://github.com/nodejs/node-gyp){:target="_blank"}, which I did not have set up on my machine.

The installation process was not too complex, it simply requires installing the package globally and installing the windows build tools (specifically on Windows, via npm).

After I managed to get the needed packages installed, I found myself running into more issues trying to try the demo, it seemed as if it did not like to load MobileNet, creating a new instance yielded results through console logs, but beyond that it broke.

After a bit of experimentation, I removed the line containing `` mn.path = `file://${path}` ``, since it the mn object already had a path linking to google, then after searching a related error in the console log, I found an [issues thread](https://github.com/tensorflow/tfjs/issues/740#issuecomment-427895896){:target="_blank"} on tfjs, which recommended modifying the code so it was as follows:

```javascript
const mobilenet = require('@tensorflow-models/mobilenet')
global.fetch = require('node-fetch')
const model = await mobilenet.load()
```

The modification being the overwrite of the global fetch, although this still left one last error, a different one from last time, being `Error: Unknown feature TENSORLIKE_CHECK_SHAPE_CONSISTENCY.`. 

A quick Google of this error lead to the same thread and a [different comment](https://github.com/tensorflow/tfjs/issues/740#issuecomment-432983629){:target="_blank"} further down, which stated the same modifications were made as above (modifying the `ms.path` and `global.fetch`), but then made the following modification:

> And then , I bump tfjs to the latest release:
>   `"@tensorflow/tfjs": "^0.13.0",`
>   `"@tensorflow/tfjs-node": "^0.1.19",`
> It works for me now.

Now when I ran `node script.js mobilenet/model.json image.jpg` through the command line, it finally yielded a prediction, due to the modification I had to make, and the code only originally being in a [GitHub Gist](https://gist.github.com/jthomas/145610bdeda2638d94fab9a397eb1f1d){:target="_blank"}, I thought I would publish it as a [GitHub Project](https://github.com/Sean12697/MobileNet-via-TensorFlowJS-in-NodeJS){:target="_blank"}, with credit to the original author and a link back to this blog post (to explain why it exsists).