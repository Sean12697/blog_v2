---
template: blog-post
title: My ideal alternative social media platform to Twitter, not Mastodon
slug: /my-ideal-alternative-social-media-platform-to-twitter-not-mastodon
date: 2022-11-07 21:39
description: Since Elon Musk recently acquired Twitter, a lot of people have
  been turning to Mastodon and Bluesky, and I've been pondering the ideal
  alternative.
featuredImage: /assets/andrei-lacatusu-photo-social-media-spanky-few-3.jpg
---
Since Elon Musk recently acquired Twitter, a lot of people have been turning to Mastodon and Bluesky, and I've been pondering the ideal alternative. This is certainly a work-in-progress blog post, which I will most likely update over the coming days as I refine my thoughts, but for now, you're welcome for the brain dump.

As I have stated in a [series of tweets](https://twitter.com/Sean12697/status/1588973206979121152), the main balance is between privacy and security over identity, verifiability, and ease-of-use. In an ideal world and as a general rule, the platform would be as open-source as possible and use asymmetric or other / better forms of encryption, making it pass most of the privacy, security, and verifiability requirements.

This is why [Signal](https://signal.org/en/) and [Keybase](https://keybase.io/) come to mind, even though they are still very centralized, even though the clients are open-source and there is a level of close-sourcing on both platforms. This could be because they are mostly messaging and private platforms and not social media platforms, which could make their implementations biased.

Similar to Keybase, it would be ideal if you could verify yourself on other platforms and services without having to enter an email address, where the "verified" tick on Twitter could be replaced by a service such as Yoti for individuals and something like Companies House for companies within the UK, for example. Meaning the verification is only based on ensuring that they are who they say they are, if they wish to reveal that and their identity.

Which leads onto another aspect I think would be ideal: rather than having one public network of verified connections, such as is the case on Keybase, you would have one completely private set of asymmetric keys (or an alternative) to create profiles which have the option to be tied to identity. Critics would say this would encourage trolling, although with so many other platforms, trolls could easily find ways to create completely new accounts, which makes the original point pointless. This would make it possible for one easily recognised identity to be present on multiple servers and be able to be cryptographically verified, which is not the case with Mastodon and Slack.

The problem is that the identity would be a private key. If asymmetric encryption were used, this wouldn't be a unique username that could be checked cryptographically by default, although this could be an easy fix.

There are still many other thoughts in my head, such as how servers would work; by default, I would think of a similar implementation between individuals of asymmetric encryption, where the owner is one individual and the original poster is another, although I can still easily see flaws in that model. Implementing a zero-trust system without immediately defaulting to blockchain is difficult, which is why this is most likely to be in the back of my mind until I resolve at least one theoretical implementation... Or I fully migrate to Mastodon, people join another platform I'm on, or things settle on Twitter.

The main difficulty I can see is social acceptance versus complete anonymity. This issue arose after the US Navy made [Tor](https://www.torproject.org/about/history/) public, which is in the best interest of the system. in which the worst of humanity could fester without proper moderation, but Navy agents could remain in plan sight, until exploits were found within the system. Current acceptable standards could be built into the core of the system. For example, if users verified their age through the external service Yoti and were under 18 years old, which is still a problem due to vendor lock-in, they could only talk to other people in the same age group. This still would question current government-per-government acceptance of such things as drug use, which is not only viewed differently per government but is also susceptible to different opinions over time as society evolves.