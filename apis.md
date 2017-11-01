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

# Roy Fielding

^ TODO image of fielding

^ This is Roy Fielding. Some of you might know who he is, some might not.

---

# Roy Fielding

> Architectural Styles and the Design of Network-based Software Architectures.

^ In 2000, Fielding submitted his Doctoral disseration. It was titled "Architectural Styles and the Design of Network-based Software Architectures." It's a good read; and something that you should read if you haven't because it was where an important idea was first defined.

---

# Representational State Transfer (REST)

^ That idea was REST and, unless you've read his thesis, it's probably quite different than you imagine. Now, I'm not going to try to explain the whole thing because I don't have the time, but let's talk about a few bits.

---

# Not Necessary

JSON and HTTP are neither necessary nor sufficient.

^ First, I'd bet that most "REST" APIs you have seen are HTTP over JSON. And that's fine. I like HTTP. I like JSON. But those items are neither necessary nor sufficient for a REST API.

---

# Hypermedia

> What needs to be done to make the REST architectural style clear on the notion that hypertext is a constraint?

^ There are a few reasons for that but the most obvious is that REST is defined as a system for distributed hypermedia. The whole thing hinges on it. As Fielding has said many times, Hypermedia Is A Constraint. So... what is it?

---

# Hypertext is...

> When I say hypertext, I mean the simultaneous presentation of information and controls such that the information becomes the affordance through which the user (or automaton) obtains choices and selects actions.

^ TODO

---

# An Aside into Affordance...

^ TODO



---

# Back to Hypertext

^ TODO



TODO
Affordances -> rest
API evolution
Contract Tests
Alternatives to REST: GraphQL
Alternatives to JSON -> HTML5

---

# Thank You

@garyfleming
