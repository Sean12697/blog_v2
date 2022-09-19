---
template: blog-post
title:  "[Hackathon #6] - GreatUniHack 18"
date:   2018-11-11 20:00
slug: /hackathon-6-greatunihack18
description: Coming Soon
---

This is the first Hackathon I have attended with a rough team, being a peer on my course ([Pritam Sangani](https://twitter.com/pritamsangani)), as well as a few ideas for what we will produce.

Originally my idea was to participate on the "Online Collaboration" track, wanting to potentially create something which was less of a tool for active productivity, but more artsy (collaborating to produce it via online means), or passively like how Google potentially uses your data if you drive (with others) to judge if there are traffic jams, displaying them on Google Maps.

But when it came to the day of GreatUniHack I had a change of mind, the night before I was looking at the sponsor's challenges and was interested in American Express's, which was to "recreate a modern website as if it were made in the 1990s", due to the fact I had watched a popular video ["If Facebook were invented in the '90s..."](https://www.youtube.com/watch?v=xrYRH3PYYT0) which was made for satire but could have been a good basis.

This idea would have been humorous but I didn't feel it was original enough to win, so I thought of doing Visa's challenge which was to create the "most innovative payment experience in a clickable or paper prototype". My idea would be to take a more human centered approach, thinking why card/online payments sometimes don't happen, gathering statistics and coming up with a solution, likely mentioning card fraud.

That particular idea came to me as the Hackathon started and we didn't want to spend too long on ideas, since even though there were likely to be less competition (which there wouldn't have been), it would have taken a few hours potentially to figure out if it were worth pursuing.

## Final Idea

Our final idea was to go with the American Express challenge, but rather than basing it on Facebook, we decided to make it for Slack, since that's what everyone was using to communicate, and rather than recreate what it looked like, we decided to imitate an IRC (Internet Relay Chat).

For this we wanted to include a few easter eggs in the form of ASCii Art, referring to the Hackathon, IRC's and others for fun, but for our MVP (Minimum Viable Product), we decided to stick with getting a vanilla chat working with SocketIO initially.

## Our Tech Stack

Both of us using Web Based technologies we used NodeJS (Express) for our core on the server side, easily interacting with it with front-end JavaScript, then other elements were to be MongoDB for our Database (using the Mongoose package), then other packages include; body-parser and bcrypt (for hashing user passwords).

## Separation of Jobs

Pritam's jobs were to handle the Express routes, when the front-end were to do API requests to the backend (getting/posting messages and logins/signups), the MongoDB itself and when it's within these requests, getting/setting the cookies, deployment from GitHub to Heroku (quite simple), then also DNS setup for the domain I bought (for 84 pence).

My roles were creating the entirety of the design elements, including the ASCii Art (mainly used from else where or converted from [picascii](http://picascii.com/)), as well as the majority of the front-end interacts / display from and to the server.

## VS: Live Share (Extension)

We both use Visual Studio Code as our IDEs (and I am using it now to write this, with "Instant Markdown" typing in another tabbed browser like a Word Document), due to this I suggested we used Microsoft's Experimental Extension life Share.

The concept is to collaborate in real time like you can on online documents through Google and Microsoft, but instead on an individuals project. Our use case was to do paired programming slightly easier, as well as working on our own parts of code, or on the same lines on a file simultaneously.

After spending many hours with it we found it very good, it was extremely responsive and fast, we found it useful that you could use the others terminal and it was blocked behind a request (meaning some cannot just join a Live Share and execute malicious commands immediately).

Although, we did suffer from it crashing every so often, not too regularly, maybe once every couple of hours or less, it was still irritating but to be fair the extension itself is still in preview, so it won't be perfect.

## Challenges

The first minor challenge we had is that neither of us had used the NodeJS package socket.io from npm before, we both had heard of it and I have seen it taught to second year Web Technology for their assignment, so I knew that was our best bet for our project, but learning how it work was new (even though it took under an hour connecting it to a database as well).

From there it was very simple and we reached our MVP within the first few hours, the next challenge came to deployment and ports, once deployed we did initially face issues with it failing to build and so on. Pritam fixed this under his roles where I was working on a different aspect of the front-end, but eventually it was fixed.

The next one after that was working out how to set up the DNS records on Namecheap to correctly direct to our Heroku application (that still could be reached from xxx.herokuapp.com), after trying a few we eventually found the correct record value to set and waited enough time for DNS servers to update (which can take a while).

After this things ran pretty smoothly until around midnight, when we were both tired and were getting slower at picking up minor mistakes. Around midnight (when it was midnight pizza) we were adding the signin/signup logic and adding a cookie from that, I had a rough idea and decided to think on it as we were having pizza.

My solution was definitely interesting, when the user wasn't logged in I pushed every word they entered into an array, checking the length and indexed elements within it to check how far along are they (if it's a length of one they should have entered either 'signin' or 'signup' in index 0, or 'arnie' for the mIRC easter egg). Pritam struggled slightly to wrap this head around this but it was getting late so we had some sleep (this function can be found [here](https://github.com/Sean12697/SlackChat/blob/master/script.js#L130) in the Github source code).

The next one came to the logic of handling multiple key presses, I implemented a solution that worked online after I added the functionality to change colours, basically having it as a CSS property that's white by default, but then using the keyboard character number as an offset (0 on the keyboard is 48 and 9 is 57) to an array of set rgb values.

Pritam offered to fixed this simple (but annoying) if statement and was due to curly brackets being needed like this: `if((e.which >= 48 && e.which <= 57) && e.altKey)`.

The final main challenge was that the screen wasn't scrolling to the bottom as new messages arrived, which was an issue UX wise since the user could not potentially not be aware of new messages. I had used a scroll snap bottom property in CSS before, but that and other workarounds didn't seem to work. Again Pritam offered to try and work it out as I add some more functionality and easter eggs, to his credit he fixed it with just under an hour to spare (within about half an hour of trying to fix it).

## Take Aways

From this hack' I came away with a better understanding of NodeJS/Express, and even more for MongoDB, Deployment (Heroku) and socket.io in terms of technical skills, my team was people I know from University, although hadn't worked with before and was a good chance to. The UoM HackSoc had been great as always and it also couldn't have been possible without the sponsors/mentors/volunteers, all of which I did try to speak to in part and made the event feel homely (especially sleeping there overnight).