---
layout: post
title: How to program a computer, for children 
---

Part 1. Instructions 

Programming a computer is a lot like writing instructions for someone really, really stupid. Imagine a person who knows nothing. They don't know how to walk, talk, read, or write. In fact, the only thing that they know to do at all is simple arithmetic. They can add, subtract, multiply, and divide any number at all. But that's all. They can't do anything else without being told how to do it. 

* Things a computer knows how to do: 1. math 

In order to get a computer to do something then, you must explain very carefully. Let's say you want to get a computer to go around the room. First you must explain to the computer what a room is. Then you must explain how to "go". Is it going to walk? Then you must explain how to walk as well. Let's give that a try. 

How to walk:

<pre>1. lean on your right foot 2. move your left foot forward 3. lean on your left foot 4. move your right foot forward </pre>

Oops, that's not how to walk. That's how to take a single step. 

That's OK though, because writing instructions for computers is like taking baby steps. In fact, this looks like pretty good instructions for taking a step. Let's make it into an object method. 

What object takes a step? It's like a riddle. But the answer is, legs take a step. So we will call the object <code>Legs </code>. 

What do the <code>Legs </code>do? They take a step. So, translate that into computerese, and we have,

<pre>Legs.takeAStep() { 1. lean on your right foot 2. move your left foot forward 3. lean on your left foot 4. move your right foot forward } </pre>

Excellent! Try it out for yourself if you like. Now, taking a step is part of the API that you can use in your instructions. So you can add the first line of your instructions.

<pre><code>1. Legs.takeAStep() </code></pre>

That's a pretty good start, but it's not going to get the computer around the room. It knows how to take a step, but it doesn't know how to walk yet. Can you tell what's next? We need to tell the computer to repeat the previous steps over and over again. Fortunately computers know how to do that too. 

* Things a computer knows how to do: 1. math 2. repeat 

So we can add another line to your instructions.

<pre>1. Legs.takeAStep() 2. repeat back to the beginning </pre>

So now what happens. Remember, the computer is very, very dull. In it's slow, plodding mind it will read the instruction 1, and take a step. Then it will read instruction 2, and repeat line 1 again. Then it will repeat it again, and again, and again. And so it will take many steps forward. 

Now we have explained to the computer how to walk. But not very well. Remember, computers are very very stupid. If they get an instruction to repeat something, they will do it over and over again ... forever! 

So now you must use your imagination, which is very important to have if you want to be a computer programmer. Imagine what will happen to the computer if you try to get it to walk around a room, using only the instructions we have written so far. 

Answer? It will walk straight forward, into the wall. And then it will bounce off the wall, and walk into the wall again and again ... forever. 

So, we must give the computer more instructions. The next thing to explain is how to avoid bouncing off the wall so many times. So let's add another step to your instructions.

<pre>1. Legs.takeAStep() 2. repeat back to the beginning 3. turn left </pre>

That's pretty good. Except there's one small problem. Can you guess what it is? 

The computer will never reach line 3. 

Why not? Because it will repeat ... forever. Only after repeating forever will it continue past line 2 and get to line 3. Forever is a long time from now. The universe might blow up by then. So now you have instructions with 3 lines, but the computer will never, ever get past the second one. This is called a bug. 

It's said that back in the old days, the first computer had big wheels and gears and glass light bulbs and electrical relays. And the computer worked really well, until one day, it stopped working. So the technicians took apart all the wheels and gears and they found that a moth had flown in and got stuck and made it stop working. This was the first computer bug. 

Nowadays, computers are smaller than bugs. But when something goes wrong, you still call it a bug. The name stuck too. 

When you get a computer bug, you need to take apart your instructions, find the part that's stuck and fix it. The first step is to the find the bug. Where's the bug in your instructions? Well, line 1 says to take a step. That seems OK. And line 3 says to turn left. That seems OK too. 

But line 2... that seems to have a problem. As we said just a minute or two ago, when the computer reads that line, it will repeat ... forever. Have you ever heard a CD skip? It goes back and plays the same bit of music over and over ... forever. Well, it's just like that. It's not good. In fact, it's bad. In fact, it's always, always a bug to repeat forever. It's also a very common bug even for the best programmers, so don't feel bad about it. 

Fortunately, computers aren't quite as stupid as I said before. They do know how to do something else. They know how to pick between two different choices. 

* Things a computer knows how to do: 1. math 2. repeat 3. choose 

Now can you think of a way to fix the bug? Well, when you explain to the computer how to walk around the room, ask it to make a choice before it repeats any step. Ask it to check and see if it's walked into a wall. It can tell if it did... but only if you ask to make a choice.

<pre>1. Legs.takeAStep() 2. if you haven't hit a wall yet, repeat back to the beginning 3. turn left </pre>
