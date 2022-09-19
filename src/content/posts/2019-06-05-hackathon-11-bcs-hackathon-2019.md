---
template: blog-post
title:  "[Hackathon #11] - BCS Hackathon 2019"
date:   2019-06-05 23:00
slug: /hackathon-11-bcs-hackathon-2019
---

This is the first hackathon I am attending along with my co-founder, [Ben Grubert](https://twitter.com/Ben_Grubert){:target="_blank"}, which is of benefit since we both complement each other in terms of skills and abilities (working well together). Due to this, we did have a few prior discussions on ideas before the hack'.

## Initial Idea

Out of the ideas we discussed, we decided to run with a gum like Aspirin solution with flavouring, with medial information on the packaging being "ONLY FOR HEART ATTACK" (along those lines). 

The idea being that it would only be used in the case of a heart attack, where it could be placed under a patients mouth and chewed, rather than being looted by anyone from a first aid box.

From there we thought we could maybe introduce it into a campaign about improving first aid boxes, either raising awareness, or how to ensure that they are stocked correctly.

There was certainly further research to be done, although we thought the best approach would be to discuss it more with clinicians at the hackathon.

## Team Building

On the day Ben gave a pitch of our idea and we then tried to recruit others onto our team, whiles doing so and talking to mentors, we found there might be a few issues with our initial idea, and we would need to refine our idea then do further research.

After discussions with a few people, our final team ended up with the following members:

- [Me](https://www.linkedin.com/in/sean12697/){:target="_blank"} (Full Stack Developer)
- [Ben Grubert](https://www.linkedin.com/in/ben-grubert-0a7b71b7/){:target="_blank"} (Manager)
- [Panagiota Mitropoulou](https://www.linkedin.com/in/panagiota-mitropoulou-5b8a92107/){:target="_blank"} (Clinician)
- [Rishabh Rawal](https://www.linkedin.com/in/rawalrishabh/){:target="_blank"} (Java Developer)

Panagiota was of particular benefit, being that she has more knowledge about the inner workings of wards also.

## Idea Refinement

After much more discussion we decided to focus on improving the first aid box, potentially making it "Smart", the idea being to comply with law and in the case of an emergency, that a first aid box would always be full to meet demand.

Going further from this we could also augment the user experience by including a phone inside the box, or a pre-recorded message for certain items, allowing those with little to no knowledge to be able to aid someone in need.

From this point there were the legal ramifications to research, what are the specific legal requirements, any prior examples of companies being sued due to non-compliant first aid boxes and also what the current systems are (for restocking).

## Research

The first piece of reseach to be done was on what specific regulations do first-aid boxes fall under, which we quickly found to be "The Health and Safety (First-Aid) Regulations 1981", where Regulation 3 (Duty of employer to make provision for first-aid) covered most of our questions.

> Every employer should provide for each work site at least one first-aid container supplied with a sufficient quantity of first-aid materials suitable for the particular circumstances.

We found many declarations like the one above, including language such as "sufficient quantity", where there was no declarative minimum for a first aid box to contain, along with this, we also found the following regulation (3.42):

> First aid at work does not include giving tablets or medicines to treat illness. The only exception to this is where aspirin is used as first aid to a casualty with a suspected heart attack in accordance with currently accepted first-aid practice. It is recommended that tablets and medicines should not be kept in the first-aid container.

Which dismisses our original idea in part since it is not recommended.

Whiles others in the team tried to find any legal cases and speak to first aiders in the building, I found there to be a recommended standard for first aid boxes (British Standard BS-8599-1), which was found just before lunch and a talk.

After lunch, we were able to talk to a first aider contracted by Manchester Central Convention Complex (where this Hackathon was held), where we noticed the first aid box he brought to us was BS-8599-1 compliant.

![GMEX First Aid Person](https://i.imgur.com/UCSCLe6.jpg)

Not only were we able to find out about how they restock the first aid boxes and have a look at their incident forms (documenting the usage of any materials), but we were also able to find that our current idea might not be completely needed.

## Pivoting Ideas

At approximately 2PM on the first day, after further discussion with the team, we decided to change ideas, switching to a patient / family empowerment platform, which is centred around decreasing patient and family stress.

This idea was very close to Ben, due to the times he has been in hospital and if this platform had existed, it would have aided in his recovery quicker.

After discussing features, viability and naming it Nestle (the definition being "settle or lie comfortably within or against something"), a couple of team members had to pop out for other meetings, which left three areas to be developed by the second day:

### Qualitative Research 

Ben lead the Qualitative Research, visiting Manchester Royal Eye Hospital to conduct surveys and doing a few interviews, which lead to the concluding that our platform is wanted and if implemented, would be used.

### Quantitative Research 

Panagiota mainly lead Quantitative Research, finding the following papers to back our idea and provide statistics for the business case (combined with figures from [NHS Reference Costs](https://improvement.nhs.uk/resources/reference-costs/){:target="_blank"}):

- Britteon et al (2017). Association between psychological health and wound complications after surgery. British Journal of Surgery.​
- Broadbent, E., Petrie, K. J., Alley, P. G., & Booth, R. J. (2003). Psychological stress impairs early wound repair following surgery. Psychosomatic Medicine.

[Ryan Kerstein](https://twitter.com/Ryan_L_K){:target="_blank"}, one of the very helpful mentors and a Surgeon, was able to bring up the statistic, although unfortunately no sources (apart from one we found previously through NHS complaints).

- 47% Increase in Surgical Complications
- 33% Complaints due to poor communication
- 70,000 Last-minute cancellations
- £1,200/hour cost to one theatre

### Base Development (Messaging Platform)

Me and Rishabh stayed until near 6PM to ensure that we has a service made that could be integrated into the platform which would send out a pair of text messages to a patient and their listed next of kin.

Using Twillio we were successfully able to send out the following pair of text messages to any given phone numbers (which would be demoed in our presentation):

- MR FIRSTNAME LASTNAME, you are scheduled for an operation in five days’ time, we suggest you click the following link to login to our new service, NESTLE.
- MR FIRSTNAME LASTNAME, a next of kin is scheduled for an operation in five days’ time, to track his progress we suggest you click the following link to login to our new service, NESTLE.

## Day 2

The focus when we arrived for the second day was to refine our research into content that we could present coherently, and also having a demo ready for a couple of judges to use.

Ben drafted up a few wireframes and UI's for me to create, which is where we also refined the user journey, how each participant (patient / next of kin) would enter the system and use it. Whiles Ben did this, the rest of us were either doing more research and refinement of the slides, or extra development.

The few hours we did have left flew by and left us a demo to present and just enough time to trial the presentation, refining aspects and choosing who would speak.

### Demo Time

Ben and Panagiota were the two from our team to speak, where I would ensure that the demo ran smoothly and both our chosen participants received the appropriate text messages to our demo service.

We listened to the other demos and felt there were many other great ideas, especially from the team [Sophie Ashcroft](https://twitter.com/ms_s_ashcroft){:target="_blank"} was on (a good friend of mine), we were quite unsure where we would place, personally I thought we were in the top three.

Once it came to the announcements... We won, with Sophie's team coming second, meaning we (Ben and Panagiota) had to present our idea again at the BCS Conference, shortly after having a small interview.

After the pitch at the conference, me and Sophie took a celebratory selfie outside, just after having group pictures taken.

![Selfie with Sophie Ashcroft](https://i.imgur.com/RYzEhAh.jpg)

We did have further discussions about developing our idea further and if possible, we definitely would be interested, especially due to it peaking interest and there being viable options in terms of further funding and rollout.

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">Congratulations to the winners of the 2019 <a href="https://twitter.com/hashtag/BCSHackathon?src=hash&amp;ref_src=twsrc%5Etfw">#BCSHackathon</a>! They have been awarded funding &amp; start-up support to pursue their idea <a href="https://twitter.com/hashtag/BCS2019?src=hash&amp;ref_src=twsrc%5Etfw">#BCS2019</a> <a href="https://twitter.com/bcshackathon?ref_src=twsrc%5Etfw">@bcshackathon</a> <a href="https://twitter.com/HealthInnovMcr?ref_src=twsrc%5Etfw">@HealthInnovMcr</a> <a href="https://twitter.com/EdwardsLifesci?ref_src=twsrc%5Etfw">@EdwardsLifesci</a> <a href="https://t.co/kHGX7gVo8L">pic.twitter.com/kHGX7gVo8L</a></p>&mdash; Novartis UK (@NovartisUK) <a href="https://twitter.com/NovartisUK/status/1136596143117389824?ref_src=twsrc%5Etfw">June 6, 2019</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
