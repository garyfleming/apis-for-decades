theme: Ostrich, 1

# APIs on the Scale of Decades

@garyfleming

^ Intro: more informal and less scripted, less prepared

---

^ Okay, so I want to talk a bit about some thoughts that I've been mulling over for a few years now on the subject of API design. "A few years" might make you think that I've got some answers to share or some unique insight; so let me start by dissuading you. I don't. There are probably some good ideas in here, and some that are a waste of time.

---

^ So Relax, it's okay. Because this is at least partially a waste of time, you can relieve yourself of the burden of focussing to hear the answers. They won't come. Instead, just let it wash over you and start that thinking process for yourself.

---

^ Really. If we can achieve anything to do, I'd like it to be that we can accept that our API designs to date are not perfect (nothing is), and that with a little time and, crucially, thinking we can improve them just a little bit.

---

# Part I: A Past of Design

^ If we're going to talk about how to improve our designs, let's talk about some design-related ideas.

---

![inline](images/screwdriver.png)

^ What is this? What is it for? Is it obvious from looking at it what it does? How it does what it does?

---

# Affordance

^ Perceptual psychologist James Gibson coined the term affordance in 1966. He used it do describe how an actor (person, animal etc) would see the actional properties of the world around them. Part of nature: not necessarily visible. Open terrain affords running. Trees afford hiding. They afford climbing. They might afford sustenance to some actors (not necessarily visible!)

---

# Perceived Affordance

^ Don Norman appropriated the term for his book, "The Psychology of Everyday Things". He later clarified that he should have used "Perceived Affordance" as his term of art: designers care that someone perceives something is possible more than whether it is.

^ To draw the line between affordance and perceived affordance, he has argued, for example, that a button on a computer screen affords touching, whether the computer is a touch-screen or not. But what we might care about is whether we believe touching the button will cause an action, and what action that will be.

---

![inline](images/floppy-disk.png)

^ So, if you saw this on a button in an app or web page with which you'd interacted, you know what the affordance is. You've been conditioned to see that this is the affordance to save what you have done. (This despite the fact that some of the youngest people here have never seen or held one of these.)

---

[.build-lists: true]

# Perceived Affordance Lends Credence to Artifice

![inline](images/floppy-disk.png)

* You don't necessarily save to a disk.
* If you did, it wouldn't be a floppy.
* If it was a floppy disk, it wouldn't just be a drawing.

^ Perceived affordance! This is *very* artificial

---

# Caveat!

^ To be clear, I'm skimming the surface and slightly misusing "affordance" for the sake of simplicity. Please feel free to read more.

---

# Part II: A Present of Design

^ Okay, let's get back to APIs.

---

# Roy Fielding

![inline](images/fielding.jpg)

^ This is Roy Fielding. Some of you might know who he is, some might not.

---

# Roy Fielding

> Architectural Styles and the Design of Network-based Software Architectures.

^ In 2000, Fielding submitted his Doctoral dissertation. It was titled "Architectural Styles and the Design of Network-based Software Architectures." It's a good read; and something that you should read if you haven't because it was where an important idea was first defined.

---

# Representational State Transfer (REST)

^ That idea was REST and, unless you've read his thesis, it's probably quite different than you imagine. Now, I'm not going to try to explain the whole thing because I don't have the time, but let's talk about a few bits.

^ Yes, I know that in this slide the title text is huge and broken up weirdly

---

# rep·re·sen·ta·
# tion

^ Aside: if you look up a word in a dictionary it often has these dots. They don't represent pronounciation. They're actually hinted places to take line breaks in constrained media (YMMV per dictionary). You might call that an affordance, if you knew what they were for.

---

# Hypermedia

> "What needs to be done to make the REST architectural style clear on the notion that hypertext is a constraint?"

^ There are a few reasons for that but the most obvious is that REST is defined as a system for distributed hypermedia. The whole thing hinges on it. As Fielding has said many times, Hypermedia Is A Constraint. So... what is it?

---

# Hypertext is...

> "When I say hypertext, I mean the simultaneous presentation of information and controls such that the information becomes the **affordance** through which the user (or automaton) obtains choices and selects actions."

^ Do we see the callback there that I so subtly placed a while back? The mechanisms to control information presented AS the information is the pretty radical thing that REST is built around. It's not the only thing, but affordance is really high up the list.

---

# Right, but what?

^ Okay, I appreciate that we're back out into the conceptual swamp at this point struggling to find land. Let's talk about one limited application of this.

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

# Make Afforded APIs

^ There's lots I don't really have time to get into on controls in APIs, but let's leave that as an exercise to the reader and move onto the next part

---

# Part III: A Future of Design

^ This is the quickest chunk at the moment, but I could see this as the biggest part of the talk at some point.

---

# Evolution

^ It's almost unheard of that APIs don't change. Most people would add versioning. Fielding (rightly, IMO) argues that that's a mistake and unnecessary in a Hypermedia world. If the forms (in the sense of data types) and links are afforded as they are presented, then a reasonable client can adapt to change. Versioning shows that you've got a non-RESTy system.

---

# Build for change

^ If we're saying that change is inevitable, then plan for it. Tell integrators that you absolutely will make changes slowly and certainly. In an internal org API, that shouldn't be much of an issue. You even have a great tool at your disposal...

---

# Consumer-Driven Contracts

^ If your org controls both ends of the wire, then write CDCs. These are tests that the client gives you detailing its expectations of how your API should work and the parts it cares about. The consumer can run against these expectations and ensure it's behaving correctly.

^ They can also give the expectations to you, so you can run them when you make changes. Something breaks? Now you know what consumer you need to speak to about how you can progress together.

---

# PART IV: Heat Death of The Universe Design


---

# Not Necessary

JSON and HTTP are neither necessary nor sufficient.

^ First, I'd bet that most "REST" APIs you have seen are HTTP over JSON. And that's fine. I like HTTP. I like JSON. But those items are neither necessary nor sufficient for a REST API.

---

[.build-lists: true]

# The Forms of Things

* Links
* Forms

^ So we want APIs that have affordance in terms of hypermedia. There are different kinds of hypermedia control that act as affordance. Hyperlinks act as ways of moving between data, as connection (where that connection could have meaning). But there's this other affordance we care about where we want (lightweight?) ways of knowing the structure of resources we want to talk about. i.e. a Person has a name which is text, an age that is a number > 0, etc

---

# JSON ... why?

^ JSON, natively, doesn't have a hypermedia link type. Various standards exist to try to patch that in, but it's missing. JSON doesn't have forms. Various standards exist to try to patch that in (but are shonkier).

---

# Anything Else We Want?

* Links
* Forms
* Human readable
* Machine readable
* Compressable?
* Lightweight Structures
* Optional Types
* Existing tooling

^ There might be other things we do want in our APIs. I asked a bunch of developers the characteristics they wanted from tools and this is roughly what I got. By Structure, they meant simple data structures to arrange things properly. Arrays, maps, etc

---

# If not JSON, then what?

^ JSON meets some of these additional requirements. Is there a better format? Something lightweight, changeable, well-understood, that has these things.

---

# HTML5 has it All

^ It has everything you'd want...

^ Am I seriously arguing for it? Hmmm... maybe... dunno. What argument would you have against it?

---

# PART TBC: NEXT ITERATION

TODO

* New structure for longer version? Pair a design/philosophy section explicitly with an implementation change section. Lead up to the html5 bit at the end.

* Ship of Theseus - paradox by Plutarch -- Gladwell golf episode had names for two interpretations
*  ufo 50. 5 devs. Fictional console with colour and sound limits. Other technical limits. 50 games. Constraints enabled going faster! 35 games made in a year or so.
*  testing: fuzzers. Force use of affordances by randomising links in test envs. Force discovery of structure by adding randomised noise; Json that looks like the real thing but isn’t  (done this before)
* transactive memory - the idea that we store our ideas and knowledge outside ourselves. I don’t need to know how a remote works if my wife knows. I don’t need to know the emotional relationships between people if someone I know and trust does it for me. This is somewhat like generic controls. Don’t need to know how to navigate a set if the server can tell me
* Talk about the intentionality of design. Leads to templating.
* Talk about some of the issues with object mappers for view generation (coupling, less clarity, undesigned). Suggest templating as an alternative.
* Alice Juarrero's work on chage and evolutionary design -- Dynamics in Action
* Tweet: "APIs are hard. They are pretty much ship now, regret later" - @Chethaase https://twitter.com/chiuki/status/927232305784950784
* Whole bunch of stuff I'm not touching (layered systems, true HATEOAS)
* Contract Tests (Currently way too quick.)
* Alternatives to REST: GraphQL
* Text Adventures as bad analogues for generic api controls
* Voice control. Limited sensible verbs. leads to RESTy design. At least helps flush out hateoas controls.
* Voice control related: chatbot. ELIZA, first "AI" chatbot. Like the quote in this article about delusional thinking: https://blog.myralabs.com/your-chatbot-needs-a-name-b8f92f337386
* "Time drags" - the past has a dragging effect on the present. From the book Time Binds, by the Queer Theorist, Elizabeth Freeman
* Cars have brakes so we can drive faster. APIs have tests (particularly contract tests) to allow us to change faster
* Japanese bullet trains exiting tunnels made a sonic boom like noise (air compression). They looked to nature for answers. Found the kingfisher -> Faster, more energy efficient, and much quieter.
* No idea the analogue of natural things for API design. Figure it out. Make a wild leap.
* Web pages as analogues of REST APIs. Discovering controls in real time. Often stateless. etc.
* Evolution does have an analogue in versioning. There was no v2 for animals, just constant evolutionary change.
* After the bit about Generic controls, expand into non-generic controls, standard resource manipulation mechanisms, and some stuff about how it's fine to expect agent domain knowledge for particular resources.
* Actual HTML5 example -- worked through. Pains etc

---

# Thank You

![inline](images/cat3.gif)

@garyfleming
