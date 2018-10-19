---
layout: post
title: Another job opening :-) iPhone developer – learn on the job
---


My iPhone custom software development business is expanding yet again and we need more part-time programmers. The <a href="/weblog/2010/2/11/job_opening_iphone_parttime_contract/">last round</a> I hired two people, now we need more. Our recent apps include Unitron's uHear to test your hearing, OurKids, the Kik chat app, and others.

You must:

<ul><li>know C, C++, pointers, object and object-relational patterns already</li><li>be ready to learn the iPhone SDK fast (we'll help)</li></ul>

I've personally been programming on the Cocoa SDK since 1998 back when it was called OpenStep, so if you can pick things up, we can get you up to speed in a few weeks.

Demonstrate your qualifications by answering 2 out of these 3 tricky questions:

[Question 1] (C Pointers) Here is some slightly odd C code, but it will produce an (int) result, provided that you make some small changes in order to make it compile. What is the result going to be, and why?

<pre>int * a = 1990;
int result = &amp;5[a];</pre>

[Question 2] (Database design) Create an entity-relationship diagram for a small subset of the Facebook database. In particular, include in your diagram:

<ul><li>User</li><li>Photo (including who is tagged in the photo)</li><li>Wall Post</li></ul>

Focus on the relationships/associations between these three objects, and only include one or two of the most important static fields (like a person's name). Make sure to indicate the cardinality of a relationship e.g. one-to-one/one-to-many/etc.

To get an idea of what I'm looking for see: <a href="http://en.wikipedia.org/wiki/Entity-relationship_model">http://en.wikipedia.org/wiki/Entity-relationship_model</a>

Here's a tool you can use to draw it online: <a href="http://www.gliffy.com/">Gliffy</a>. Then just send me a screenshot. Or feel free to use ASCII art or draw on a piece of paper and photograph/scan, as long as it's very clear.

[Question 3] (C++ Objects) The C++ program below has just 2 compile time errors, 1 runtime error, and there is 1 single line missing. Send us a fixed version that compiles and runs correctly. The errors will test your knowledge of object use and management in C++, and the missing line will test you on abstract/virtual inheritance.

SEND TO: simon@semacode.com. Include your answer(s) and some source code that you have written, whether it's open source, for assignments, for fun, or whatever.

REMUNERATION: Competitive.

MORE INFO: <a href="http://simonwoodside.com/pages/consulting">http://simonwoodside.com/pages/consulting</a>

(PS Please keep the answers to yourself)

<pre>//// File: futurama.cpp ////
#include &lt;iostream&gt;

class Drinker {
public: Drinker(); void drink( int potency ); int _numberOfDrinksSoFar;
private: virtual int cantDrinkAnyMoreThan() = 0;
}; Drinker::Drinker() { _numberOfDrinksSoFar = 0; }
class Robot : public Drinker { int cantDrinkAnyMoreThan() { return INT_MAX; } };
class Human : public Drinker {
};
void Drinker::drink( int potency ) {
&#160; _numberOfDrinksSoFar += potency;
&#160; if( _numberOfDrinksSoFar &gt; cantDrinkAnyMoreThan() ) { std::cout &lt;&lt; "I'm all done." &lt;&lt; endl; }
}

int main (int argc, char * const argv[]) {
&#160; int beer = 5, coffee = 3;
&#160; Human fry;
&#160; Robot * bender;
&#160; for( int i=0; i&lt;6283; i++ ) { bender.drink(beer); }
&#160; for( int i=0; i&lt;100; i++ ) { fry.drink(coffee); }
&#160; std::cout &lt;&lt; "Bender: " &lt;&lt; bender-&gt;_numberOfDrinksSoFar &lt;&lt; "&#160; Fry: " &lt;&lt; fry._numberOfDrinksSoFar &lt;&lt; std::endl;
&#160; fry.drink(1);
&#160; return 0;
}</pre>
