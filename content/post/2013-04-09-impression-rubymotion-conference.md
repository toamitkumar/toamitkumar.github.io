---
showonlyimage: true
title:      "My Impression at #inspect2013 - RubyMotion Conference"
subtitle:   ""
excerpt: "First RubyMotion comference - observation, community contribution, trends, reactions"
description: ""
date:       2012-05-30
author:    Amit Kumar
image: "img/guard-rail-autonomy-1.jpg"
draft: false

tags:
    - conference
    - rubymotion
    - open source
    - community driven

categories: [ Tech ]
URL: "/2013/04/09/ruby-motion-conference/"
---


The first RubyMotion Conference [#inspect2013](http://www.rubymotion.com/conference/#schedule) happened in Brussels, Belgium. It was a very well [organized conference](http://eventifier.co/event/inspect13/), lots of talented people, awesome speakers, good food and yes _Belgian Beer_

![](/img/one_man_army-laurent.png)

Many thanks to Laurent Sansonetti ([@lrz](https://twitter.com/lrz)) for organizing the first RM conference.

The general [gist](https://gist.github.com/ryansobol/5276501) of what happened there. Below are my observations and opinions.

## What I saw at #inspect2013 - RubyMotion conference?

For people who don’t know about RubyMotion:

> - [About RubyMotion](http://www.rubymotion.com/developer-center/)
> - http://rubysource.com/laurent-sansonetti-on-rubymotion-internals/
> - http://motioncasts.tv/
> - https://vimeo.com/61255647

## Observations/Opinions:

### The Community:

Community plays a very important role in the success of Open Source Software. Even though RM is licensed, it has blessings from Ruby Community.

Rubyists (including me) who have tried Obj-C in the past have found it verbose and complex. We all embraced RubyMotion because of its simplicity and more important being a developer friendly language - Ruby.

At the conference I saw a lot of seasoned Obj-C developers who had tried RM and loved it. Now, they are using it for full fledged production applications. One of the big reason for this is Cocoa-Pods. They can still use their legacy Obj-C code / project in new a RM application. The build system takes care of linking and tying them during compilation. No need to re-invent the wheel, utilize the investment people have already done in iOS world. This is an interesting phenomenon because this is going to push the toolchain to next level.

### Contribution:
It is less than a year and the RM community has grown exponentially from few rubyists to thousands of iOS developers. There has been tremendous contribution by people to build ruby-motion gems/libraries/wrappers around verbose Obj-C code.The list is very big but I should definitely mention: rubymotion-wrappers.com

A lot of talks at the conference were about these libraries and wrappers.

### Focus on testing:
Ruby Community has successfully induced the importance of testing the code. Though RM comes bundled with a testing framework, its hard to do UI testing on iOS and Obj-C has suffered a lot because of this.

At the same time, it is unusual that Rubyists would not explore options to test their code on iOS platform.

In the conference I got to learn some awesome frameworks out of which ‘motion-calabash’ is really good. It gives you BDD style testing similar to what we are familiar in Ruby/Rails world - Cucumber.

You should definitely checkout https://github.com/calabash/motion-calabash . A sample [app](http://github.com/krukow/motion-calabash-inspect2013)

```
The one thing I would like to explore is the possibility to test my HTML5 phone-gaped application using 'motion-calabash'.
```

When I am developing for mobile platform I miss Chrome Developer Tools a lot. Not any more. It blew my mind to see the demo by Colin Gray (@colinta). Motion-Xray: An iOS Inspector that runs inside your app, so you can debug and analyze from your device in real-world situations. It is amazing, go [check it out](https://github.com/colinta/motion-xray)

### Broader Reach:
I was completely stunned to see presentation in a technological event by a visually impaired (I don’t mean to hurt anyone. I had never seen such a thing happening and it was a complete jaw-drop for me). Let me introduce [Austin Seraphin](http://behindthecurtain.us/about/) . He is an iOS developer and iOS Accessibility Expert. He explains how iPhone and Accessibility changed his life. A completely new perspective. His slides if you are interested - I would urge to have a look at them.

### Trend and My Reaction:
Laurent was the last to present at the conference - a noble decision I would say. He talked about roadmap and the future of RubyMotion. I see a focus shift to make the toolchain more developer friendly.

#### Some highlights:
- **High-level debugging support**: right now it uses GDB technology which is pretty low-level.
- **Documentation**: add more documentation to make it easier for newbies.

I definitely feel RM is going to change the way we are used-to doing native iOS development. So, don’t delay, hack and be awesome.

Finally, here is the presentation (Building Interactive Data Visualization Charts) [@rubymotion](http://lanyrd.com/2013/inspect/) conference:


