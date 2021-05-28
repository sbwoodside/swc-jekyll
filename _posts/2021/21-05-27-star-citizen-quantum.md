---
layout: post
title: Star Citizen's Tony Zurovec describes a scalable simulation based on real world quantum mechanics
image: 2021/star-citizen-probability-volumes.png
---

It's a lot of fun to watch Tony Z, the head of their Persistent Universe group, talk about his latest wizardry. I've [written about Star Citizen before](/2019/09/29/star-citizen-video-game.html), so I won't rehash the introduction. As I wrote before, the greatest thing about SC is that it's a sandbox game. You can go anywhere, do anything, live a life, [grow old and die](https://robertsspaceindustries.com/comm-link/engineering/12879-Death-Of-A-Spaceman), all the best parts of old school D&D sandbox games like I used to play as a kid.

But how do you simulate an entire universe, that they say will consist of hundreds of star systems? Keeping track of billions of NPCs would be a computational nightmare, nigh-on impossible.

This is where the [latest video by Tony Z on Quantum, Quasar, and Virtual AI](https://www.youtube.com/watch?v=2muGWtX8e7g) comes in. It's forty minutes of geeky awesomeness, and I love that he gets into the details, explains it intelligently, and has great visual aids. He describes a system called Quantum, and the name isn't just a trendy reference to cutting edge science (like the "quantum drive", which has nothing to do with real physics as far as I know).

Tony Z introduces the Quantum system and a simulation of hundreds of thousands of lightweight AI called Quanta.

[Quantum mechanics is deeply weird](https://en.wikipedia.org/wiki/Quantum_mechanics). With the development of quantum mechanics in the 20th century, scientists discovered that particles like electrons don't have concrete position (for example). Instead it turns out that they can only behave statistically, like rolling dice. Indeed, Einstein disliked quantum mechanics so much that he said "God does not play dice with the universe". The dice rolling comes in when someone observes a particle — this resolves the probabilities into a concrete position. In addition particles continuously appear and disappear as if by magic — these are called virtual particles.

Star Citizen's Quantum is based on the same concept. It has "probability volumes" — areas on planets, stations, and space, that have certain statistical chances of things happening. For example, in some area of space, there could be a 50% chance of encountering a pirate. When you enter that space, Quantum flips a coin, and if it comes up heads, then you encounter a pirate.

That pirate gets created as you enter the space, and moves from a Quanta (a very lightweight AI) to a Virtual AI (an intermediate AI) and then finally a so-called Subsumption AI which is fully rendered in the game and moves around in precise ways — similarly to how real quantum particle goes from being in a statistical existence to a concrete position when it's observed.

As Tony Z said: "These areas are called probability volumes and the important thing to note is that the NPCs they create are ephemeral. They pop into existence for a brief moment so the area you are viewing looks like what Quantum says it should. And once they're sufficiently far from any players, are completely and forever destroyed."

Because Quanta are so simple, the game can simulate them in very large numbers, giving the game a complete simulated economy and society. The benefit of this is the efficiency and scale. Even a medium-scale "Virtual AI" as described by Tony Z is too complex to have millions of them running all the time. Quantum means that the game can just keep track of the much smaller number of probability volumes — calculating the events going on in each volume all in one lump. It only needs to become specific when a player looks at some specific NPC or information.

Star Citizen is still a way off from being released, but it's well funded and making steady progress towards an ambitious goal. The Quantum system is a cleverly-designed system for creating a true sandbox universe, based on the real world quantum mechanics.

If you're interested in a great (if challenging) read on quantum mechanics, check out the book [QED: The Strange Theory of Light and Matter](https://en.wikipedia.org/wiki/QED%3A_The_Strange_Theory_of_Light_and_Matter) by Richard Feynman.
