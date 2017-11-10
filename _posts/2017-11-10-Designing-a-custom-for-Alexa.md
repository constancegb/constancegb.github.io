---
layout: post
title: Designing a custom skill for Alexa
---

In a precedent post, I wrote about my experience on developing a Trivia skill for Alexa, following an Amazon-Developers-made tutorial. Today we take it to the next level by developing our own non-trivia skill from scratch. Specifically, this post intents to show you the underlying design process of the skill.


**Coming up with a good skill idea**

If this is the first time you develop an Alexa skill, there are some best practices to keep in mind while designing your idea.

The whole point of voice-interaction-based services is that it considerably simplifies the user's relationship with technology. Instead of previously having to physically interact with various devices, the user is now able to be hand-free while using his voice to order a pizza or a cab, asking for weather reports, take notes, and so on.

>"In the case of voice, less is more." - Ankur Prasad, Developer Relations and Outreach, Amazon Appstore.

What does this means for us, developers? When designing your Voice User Interface, you have to be able to deliver your service to the end user with a minimum of back and forth interactions with Alexa, otherwise the user will be confused and you will lose engagement. The best skills are able to do so with only one-level-deep interactions, meaning that the user directly gets the information he or she was looking for, without the need for Alexa to respond by asking for specifications relative to the user's request.

With that in mind, I decided to develop a skill that would advise the user what to wear depending on the weather. Here, you notice that Alexa will be able to deliver the expected piece of information just upon the user's request.


**Designing the voice interaction menu**

Several choices have to be made relatively to the intent schema, slots & utterances. If you are unfamiliar with those terms, now might be a good time to read through these Amazon Developers resources on custom skills: https://developer.amazon.com/docs/custom-skills/understanding-custom-skills.html

In my case, the choices concerned the location and the date & time for which the dressing advice is wanted. I chose to have the location not as a slot, but set by default; this means that Alexa will use the Echo's location to access a specific weather forecast and deliver the dressing advice accordingly.

As for the date and time, for the sake of simplicity, I decided that my skill will be able to deliver a dressing advice either for the rest of the day the user made the request on, or just for the day after. Once again, this could have been done with date as a slot, or as two different intents. I selected the second option, writing my utterances so that if the user does not specify 'today' or 'tomorrow' in his request, it will default to today.

{:.center}
![]({{ site.baseurl }}/img/menu-representation.png)
