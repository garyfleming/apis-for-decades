theme: Ostrich, 1

# APIs on the Scale of Decades

## @garyfleming

^ Intro: more informal and less scripted, less prepared

^ TODO ADD AN IMAGE AS THE BACKGROUND

---

![inline](images/apis-are-hard.png)

---

# A Long Time Ago...

^ TODO story about legacy system

---

# What do we want in an API?

* Machine and human readable
* Changeable
* Testable
* Documented

---

# Part I: What can you Afford?


---

![left fit](images/mario03.png) ![right fit](images/GroundPoundSwitch.png)


---

![left fit](images/mario03.png) ![right fit](images/Mandibug.png)

---

# Affordance

^ Perceptual psychologist James Gibson coined the term affordance in 1966. He used it do describe how an actor (person, animal etc) would see the actional properties of the world around them. Part of nature: not necessarily visible. Open terrain affords running. Trees afford hiding. They afford climbing. They might afford sustenance to some actors (not necessarily visible!)

---

![](images/cat-tree.jpg)

---

![](images/bird-tree.jpg)

---

![](images/sloth-tree.jpg)

---

![](images/sloth-face.jpg)

---


# Perceived Affordance

^ Don Norman appropriated the term for his book, "The Psychology of Everyday Things". He later clarified that he should have used "Perceived Affordance" as his term of art: designers care that someone perceives something is possible more than whether it is.

^ To draw the line between affordance and perceived affordance, he has argued, for example, that a button on a computer screen affords touching, whether the computer is a touch-screen or not. But what we might care about is whether we believe touching the button will cause an action, and what action that will be.

---

![inline](images/floppy-disk.png)

^ So, if you saw this on a button in an app or web page with which you'd interacted, you know what the affordance is. You've been conditioned to see that this is the affordance to save what you have done. (This despite the fact that some of the youngest people here have never seen or held one of these.)

---

[.build-lists: true]

![fit](images/floppy-disk.png)

* You don't necessarily save to a disk.
* If you did, it wouldn't be a floppy.
* If it was a floppy disk, it wouldn't just be a drawing.

^ Perceived affordance! This is *very* artificial


---

# Caveat!

^ To be clear, I'm skimming the surface and slightly misusing "affordance" for the sake of simplicity. Please feel free to read more.

---

# Roy Fielding

![right fit](images/fielding.jpg)

^ This is Roy Fielding. Some of you might know who he is, some might not.

---


> "Architectural Styles and the Design of Network-based Software Architectures."

^ In 2000, Fielding submitted his Doctoral dissertation. It was titled "Architectural Styles and the Design of Network-based Software Architectures." It's a good read; and something that you should read if you haven't because it was where an important idea was first defined.

---

# Representational State Transfer (REST)

^ That idea was REST and, unless you've read his thesis, it's probably quite different than you imagine. Now, I'm not going to try to explain the whole thing because I don't have the time, but let's talk about a few bits.

^ Yes, I know that in this slide the title text is huge and broken up weirdly

---

# rep·re·sen·ta·
# tion·al

^ Aside: if you look up a word in a dictionary it often has these dots. They don't represent pronounciation. They're actually hinted places to take line breaks in constrained media (YMMV per dictionary). You might call that an affordance, if you knew what they were for.

---

# Hypertext is...

> "... the simultaneous presentation of information and controls such that the information becomes the **affordance** through which the user [...] obtains choices and selects actions."

^ Do we see the callback there that I so subtly placed a while back? The mechanisms to control information presented AS the information is the pretty radical thing that REST is built around. It's not the only thing, but affordance is really high up the list.

---

# Wut?

![original](images/wut-cat.jpg)

^ Okay, I know the last few slides have been fairly information dense. So let me simplify

---

# Information + Controls = Better API

^ Let's make this clear. You put your mechanisms for controlling your API into the information returned by your API. You don't separate them out.

---

# Example pls

![](images/curious-cat.jpg)

---

[.build-lists: true]

# Collections

* Next, previous, start, end
* Filter
* Sort By...
* Group By...

^ This is the most common place you'll see controls in REST, because it's conceptually simple, very generic, and makes life easier for integrators.

^ When we have large data sets we want to share with the world, we often don't want to just do a huge data dump. We use affordances to offer options for navigating through datasets.

---

# HAL-style

```javascript
{
  "items": {
    ...
  }
    "_links": {
        "next": { "href": "/page=2" }
    }
}
```

^ This is just a quick syntax example. I don't think I've seen any "standard" JSON syntax for this that I particularly like, but some are better than others.

---

# Generic

^ These are really generic collection affordances. It doesn't matter what the underlying items are, the affordances should work. REST puts a lot of emphasise on standard controls when possible.

---

# Text Adventures

![fit original](images/text-adventure.gif)

^ If you ever played an old text adventure, there will usually a bunch of standard verbs you could use
against the nouns. But these were domain specific. "Go north", "turn wheel", "kill dragon"

---

![](images/kill-jester.jpg)

^ "kill-jester"

---

# Domain Knowledge is Okay

![](images/sloth-tree.jpg)

^ It's fine to use domain specific verbs and nouns to describe affordances. It's okay to expect agents to only understand the controls you're offering alongside the information if thye understand the domain itself.

---

# Alexa search for...

![fit ](images/echo.png)

^ A good way of finding those verbs and nouns is imagining a voice interface. How would you want to ask
Siri/Alexa to do what you want to do? Offer *that* to your users alongside the info.

---

# Part II: Change

^ So I've talked a lot about affordance and controls because I think it underpins most of everything else. One of the other things people wanted was for things to be safe to change. How do we do that?

---

# Ship of Theseus

![fit](images/ship.png)

---

# Bullet Trains

![](images/bullet-train.jpg)

^ Tunnels, sonic booms, re-engineering. Kingfishers. No splashes. No sonic boom.

---

# Biomimicry

^ We know that we can see incredible designs in nature. Evolution has produced some fantastic fits
for what makes sense to us. I'm going to suggest we mimic an aspect of evolution

---

# Owl V2

![fit](images/owl-v2.png)

^ There was no owl v2. Or v3. Instead we had simple birds becoming more specialised over Time
until we had the owls we have today. The owls in a millenium from now will be different. They'll still
be owls.

---

# Affordance Trumps Versioning

^  if we present the controls we can use on a piece of information as part of that Information
then we don't need versions. We just change the affordance we make available.

---

# You Deal With This Every Day

![](images/web-page.png)

^ You visit web pages and deal with the links they throw up. You never concern yourself with whether you're viewing google V1, v2, or v1000000.

---

# PART III: Testing

---

# Build for change

![fit ](images/screwdriver.png)

^ If we're saying that change is inevitable, then plan for it. Tell integrators that you absolutely will make changes slowly and certainly. In an internal org API, that shouldn't be much of an issue. You even have a great tool at your disposal...

---

# Consumer-Driven Contracts

^ If your org controls both ends of the wire, then write CDCs. These are tests that the client gives you detailing its expectations of how your API should work and the parts it cares about. The consumer can run against these expectations and ensure it's behaving correctly.

^ They can also give the expectations to you, so you can run them when you make changes. Something breaks? Now you know what consumer you need to speak to about how you can progress together.


---

[.build-lists: true]

# Fuzzers

* Modify parts without contract coverage
* Scramble links
* Add in dummy data


---

# PART IV: A NEW OLD API

^ TODO use examples above and elsewhere to argue against JSON. Argue for HTML5

^ So far I've argued for affordances, presenting information and tests together.

---

# The Forms of Things

* Links
* Forms

^ So we want APIs that have affordance in terms of hypermedia. There are different kinds of hypermedia control that act as affordance. Hyperlinks act as ways of moving between data, as connection (where that connection could have meaning). But there's this other affordance we care about where we want (lightweight?) ways of knowing the structure of resources we want to talk about. i.e. a Person has a name which is text, an age that is a number > 0, etc

---

# JSON ... why?

^ JSON, natively, doesn't have a hypermedia link type. Various standards exist to try to patch that in, but it's missing. JSON doesn't have forms. Various standards exist to try to patch that in (but are shonkier).

---

# What do we want in an API?

* Machine and human readable
* Changeable
* Testable
* Documented

----

# Anything Else We Want?

* Links
* Forms
* Compressable
* Lightweight Structures
* Optional Types
* Existing tooling

---

# HTML5 has it All

^ It has everything you'd want...

^ Am I seriously arguing for it? Hmmm... maybe... dunno. What argument would you have against it?

---

# You Deal With This Every Day

![](images/web-page.png)

^ Those links, the forms, the domain knowledge. You deal with it every single day. GitHub **is** an API. It's an
interactive toolset. You have domain knowledge. You can figure it out.

---

# Thank You

![left](images/cat3.gif)

## @garyfleming

---

# Thank You

## @garyfleming

## github.com/garyfleming/apis-for-decades/
