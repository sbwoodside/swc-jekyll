---
layout: post
title: Closures with return values in Java
---


Here's how to get everything you need from closures today in Java, without waiting for the big foreheads to argue over how to make it nice and perfect.

You've almost certainly used something sort of closure-like when you've used the Runnable interface. You can for example create an anonymous subclass of Runnable and .run() it:

<pre>  Runnable closure = new Runnable() {<br />   &#160;void run() { System.out.println("Hello"); }};<br />  closure.run(); // prints Hello</pre>

In particular in Java Thread class implements Runnable. You can do more interesting things, for example:

<pre>  StringBuffer _myString = new StringBuffer("Hello");<br />  // Java will only close around final variables because it's dumb<br />  final StringBuffer foo = _myString;<br />  Runnable closure = new Runnable() {<br />    public void run() { System.out.println(foo); }<br />  };<br />  closure.run(); // prints Hello</pre>

This is why it's called a closure -- the anonymous subclass Closes Around the variables in the scope in which it's defined. So, it has access here to myString. If you change _myString in the original context the closure will use the new value.

You can pass closures around, for example pass it to another method in another class, and it will still remain closed around the Original context. Like this:

<pre>  public void anotherContext( Runnable closure ) {<br />    StringBuffer foo = new StringBuffer("Goodbye");<br />    closure.run(); // still prints Hello from its own context<br />  }</pre>

This is all available out of the box in Java, a little boring. It would be interesting if the closure could work on variables BOTH from its original context and that you pass into it at the same time. This can be done, but Runnable doesn't allow it, so we'll make our own Runnable:

<pre>// A general-purpose closure class that can receive and<br />//   return values when you call it.<br />// This is an abstract class... override these functions for<br />//   whatever kind of closure you need.<br />// If you call a non-overriden function, it will throw you.<br />public class SemaRunnable {<br />  public void run() { throw new RuntimeException("Must override SemaRunnable.run()"); }<br />  public Object run( Object param ) { throw new RuntimeException("Must override SemaRunnable.run()"); }<br />}</pre>

Now I can do a simple example (from the <a href="http://en.wikipedia.org/wiki/Closure_%28computer_science%29">Wikipedia article</a>):

<pre>SemaRunnable bestSellingBooks = new SemaRunnable() {<br />  public Object run( Object thresholdObject ) {<br />    int threshold = ((Integer)thresholdObject).intvalue();<br />    // assume bookList is in the local context:<br />    myBookList = bookList.booksWithSalesGreaterThan(threshold);<br />    return myBookList;<br />  }<br />};<br />// call books = bestSellingBooks.run( Integer(5000) );</pre>

Here's a more complete example. In some code I'm working on, I need to pass an image -- not just an image, but also the ability to get just a subImage of that image. I don't want them to have to know how to do image manipulation. Here is how I do it using closures:

<pre>&nbsp;&nbsp;&nbsp; SemaRunnable getSubImage = new SemaRunnable() {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; public Object run( Object param ) {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; int x = Array.getInt(param,0); // these four variables<br />       &nbsp;int y = Array.getInt(param,1); // are coming in<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; int width = Array.getInt(param,2); // from the<br />       &nbsp;int height = Array.getInt(param,3); // caller<br />        // Now I will close on a method in my local context:<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; short[] subImg = dataForSubImage( x, y, width, height );<br />        return subImg;<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }<br />&nbsp;&nbsp;&nbsp; };<br />    someObject.setClosureToBe(getSubImage);<br /><br />...<br /><br />  // This method is being closed upon in the local context:<br />  public short[] dataForSubImage( int x, int y, int width, int height ) {<br />    ...</pre>

someObject in some completely different part of my code, gets the closure and calls it like this:

<pre>  // completely different class, which received closure object<br />  int [] subImageData = (int[])closure.run( new int [] {new_x, new_y, new_w, new_h} );</pre>

You don't have to call it closure. And you can pass as many params either way as you like, storing them in arrays, since array is an Object in java.

<strong>But... but... but...</strong>, people will say, why not create a class which does this, and import the class, and construct the class, and make calls on the class, it would do the same thing. They just answered their own question: it requires lots of LOCs.

And there's other good reasons. For example, let's say you have two versions of your function for different situations, you can simply swap them out of they are closures. The beauty of it is, the java compiler doesn't know or care what's happening, because everything is just SemaRunnable and Object. So it's not going to complain that a function or class name has changed. That means metaprogramming goodness. Sweet.

So, practical closures in Java. It may look a little unfamiliar at first, but once you know how to do it it's easy and can be really useful.

<strong>EXTRA SPECIAL BONUS</strong>: An implementation of the full monty, closure that takes a closure, makes a new closure from it, and returns that. I promised myself I'd go to bed early, but instead I stayed up and wrote you this code which is guaranteed to actually work, because I tried it. Try running it.

<pre><br />// By: Simon Woodside sbwoodside (a)(t) gmail (d)o(t) com<br />// See: http://simonwoodside.com/weblog/2009/7/7/a_little_bit_more_serious/<br /><br />// To try this out:<br />// % javac Test.java &amp;&amp; java Test<br /><br />// Demonstration of how to do closures in Java<br />// In this case, |derivative| is a closure which approximates derivatives, and<br />// |sineDerivativeApproximator| approximates the derivative of ... you guessed it ... sine.<br /><br />// It's hard to believe, given how much code there is, but in javascript this would be:<br />// function derivative(f, dx) {<br />//   return function(x) {<br />//     return (f(x + dx) - f(x)) / dx;<br />//   };<br />// }<br />// (See http://en.wikipedia.org/wiki/Closure_(computer_science) )<br /><br />import java.util.*;<br />import java.lang.reflect.*;<br />import java.lang.*;<br /><br />public class Test {<br />  public static void main (String args[]) {<br />    System.out.println("Closures coming up!");<br />    Test test = new Test();<br />    test.go();<br />  }<br />    <br />  // SemaRunnable is a general-purpose closure class that can receive and<br />  //   return values when you call it.<br />  // This is an abstract class... override these functions for<br />  //   whatever kind of closure you need.<br />  // If you call a non-overriden function, it will throw you.<br />  public class SemaRunnable {<br />    public void run() { throw new RuntimeException("Must override SemaRunnable.run()"); }<br />    public Object run( Object param ) { throw new RuntimeException("Must override SemaRunnable.run()"); }<br />  }<br />  <br />  void go() {<br />    // Let's start with a really simple example.<br />    // See my blog post for more details:<br />    StringBuffer _myString = new StringBuffer("Hello");<br />    final StringBuffer foo = _myString;<br />    Runnable closure = new Runnable() {<br />      public void run() { System.out.println(foo); }<br />    };<br />    closure.run(); // prints Hello<br />    <br />    // Now let's do something more fun.<br />    // A closure that receives a closure and returns a new closure.<br />    // This is going to be wordy because Java Arrays and Number objects are TERRIBLE<br />    <br />    // Return a function that approximates the derivative of f<br />    // using an interval of dx, which should be appropriately small.<br />    SemaRunnable derivative = new SemaRunnable() {<br />      public Object run( Object params ) {<br />        // params must be { SemaRunnable f, Float dx }<br />        final SemaRunnable f = (SemaRunnable)Array.get(params,0); // get f<br />        final float dx = ((Float)((Object[])params)[1]).floatValue(); // get dx<br />        SemaRunnable approximator = new SemaRunnable() {<br />          public Object run( Object xFloat ) {<br />            float x = ((Float)xFloat).floatValue();<br />            float fOfXPlusDx = ((Float)f.run( new Float(x + dx) )).floatValue();<br />            float fOfX = ((Float)f.run( new Float(x) )).floatValue();<br />            float answer = (fOfXPlusDx - fOfX) / dx;<br />            return new Float(answer);<br />          }<br />        };<br />        return approximator;<br />      }<br />    };<br />    // Now create a closure that will simply return the sine(x):<br />    SemaRunnable sineClosure = new SemaRunnable() {<br />      public Object run( Object xFloat ) {<br />        double sine = Math.sin( ((Float)xFloat).floatValue() );<br />        return new Float(sine);<br />      }<br />    };<br />    // And finally put it all together:<br />    SemaRunnable sineDerivativeApproximator =<br />      (SemaRunnable)derivative.run( new Object [] { sineClosure, new Float(0.001) } );<br />    for( double x = 0.0; x&lt;3.1416; x+=0.1 ) {<br />      Float result = (Float)sineDerivativeApproximator.run(new Float(x));<br />      System.out.println( "Sine(" + x + ") = " + result );<br />    }<br />  }<br />}</pre>

I ran out of time to demonstrate this, but you can also modify variables in the context from inside the closure, even though they are final, by creating a final array containing the variable, and then modifying the object contained in the array. It's not pretty but it works.
