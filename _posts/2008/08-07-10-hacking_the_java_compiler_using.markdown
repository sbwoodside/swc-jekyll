---
layout: post
title: 'Hacking the java compiler: using anonymous subclasses as closures'
---


UPDATE: new more comprehensive post on this subject: <a href="http://simonwoodside.com/weblog/2009/7/7/a_little_bit_more_serious/">Closures with return values in Java</a>.

In Java, closures/first-order functions are not a language feature. However, as everyone knows, you can effectively get a first-order function by using an anonymous subclass instead. Something like this:

<pre><br />class MyClosure {<br />  void run() {} // override this<br />}<br />void doSomethingClosureLike() {<br />  MyClosure closure = new MyClosure() { void run() { System.out.println("We're inside a closure!"); }};<br />  runTheClosure(closure);<br />}<br />void runTheClosure(MyClosure closure) {<br />  closure.run();<br />}<br />// will print We're inside a closure!</pre>

Anyway, it's simple enough, you pass the class instead of the function and there's a little extra verbage but it works!

Also you get closure-like functionality, because inside run() you can access variables from outwhere where you created it. E.g.:

<pre><br />void doSomethingCooler() {<br />  final String myString = "Foo!";<br />  MyClosure closure = new MyClosure() { void run() { System.out.println("The string is: " + myString); }};<br />  runTheClosure(closure);<br />}<br />// will print The string is: Foo!</pre>

You can also access global variables that change over time, and the closure will use whatever is the current value WHEN THE CLOSURE RUNS.

There's just one small annoying thing, which is this particularly annoying compiler message:

<pre>local variable (WHATEVER) is accessed from within inner class; needs to be declared final</pre>

If you were do change myString to not be final, you'd get that error. Bummer. You could make myString a global variable and that would work, but that's stupid. There is a better way. Try this: <strong>UPDATE: This doesn't work, see new version at the bottom, thanks commenter the.d-stro.</strong>

<pre>void doSomethingCooler() {<br />  String myString = "Foo!";<br />  final String myStringFinal = myString;<br />  myString.concat(" Bar!");<br />&#160; MyClosure closure = new MyClosure() { void run() { System.out.println("The string is:" + myStringFinal); }};<br /> &nbsp;runTheClosure(closure);<br />}<br />// will print Foo! Bar!</pre>

Now you can even change myString after you assign myStringFinal, because Java, although they say it doesn't use pointers, really does use pointers. I.e. it passes by reference. So, myStringFinal is actually just a reference to myString, and keeps pointing to it even when you change the contents of myString.

You can CHANGE it (like using concat()) but you CAN'T reassign it. That will break the pointers. It makes sense if you think about it -- myString will have a new memory address, and myStringFinal will still be pointing to the old memory address (and the old string value). So, this won't work:

<pre>myString = "won't work"; // breaks myStringFinal</pre>

You can use this technique with any object (but not primitives like int).

<strong>UPDATE</strong>

The last source block is wrong because java Strings are immutable. Here's an example that will work as advertised:

<pre><br />  void doSomethingCoolest() {<br />    StringBuffer myString = new StringBuffer("Foo!");<br />    final StringBuffer myStringFinal = myString;<br />    myString.append(" Bar!");<br />    MyClosure closure = new MyClosure() { void run() { System.out.println("The string is: " + myStringFinal); }};<br />    runTheClosure(closure);<br />  }<br />  // will print The string is: Foo! Bar!</pre>
