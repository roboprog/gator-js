# gator-js
JS rich client library allowing easy mockup, but using a functional programming back end style

THERE IS NO CODE FOR THIS YET.  JUST SOME NOTES.  CHECK BACK AGAIN SOME DAY :-)

## Why "Gator"?

It's a pun on "delegator".

The idea is for the library to have a "Redux" style core
that has a series of "state" objects which reduce a series of events.
From the viewpoint of application controller functions,
data is immutable,
so as to make it easier to debug what happens when an event is handled.

The library and the application code can delegate to each other, 
or from one "controller" function to another.
Also, *you* get to chose whether you want an HTML mockup in
which controller functions event annotations (TBD) are attached, *or*,
if you want the view/template to be provide by the controller function,
"component" style.  It's up to you!

## Why yet another JS library / framework?

Google and Facebook have both a lot of resources, and very large scaling challenges.
Most little applications / prototypes do not.
Most of us are simply trying to stand up something quickly,
with some emphasis on it still working correctly
as well as being able to come back to it after 6 months and still
make sense of it without too much effort.

Gator is not going to try to solve the world's problems, just a few common ones.
I expect you will still be using jQuery (or other libraries) directly here and there at times,
and that's OK.
I don't want a framework with a massive amount of detail for the newbie to learn,
nor with a massive tooling debt.
If you want to include a Node back-end process, great.
If you want to just include a few scripts at the top of your utility page
and be done with things, that's fine, too.

I mentioned Redux earlier.  I like that approach.
I'm not very fond of the React mutable component class approach.
Over the last 10 years,
I have become less enamored by the "Simula 67" (which begat C++, which begat Java...) approach,
and more interested in the Lisp/Scheme approach, 
since we have good garbage collected platforms now (unlike back in the 80s).

Some approaches to be embraced in Gator:
* Avoid transpiling
  * Again, keep a light touch.  Even JS 5.1 is quite powerful.  (TBD - use some ES2015 features???)
* Higher order functions
  * Avoid classes for APIs with a single public method.
  * Partial function application
* Dynamic values - property lists as objects.
  * Still immutable, though.
  * IDEs are good at type inference - exploit that.
* TODO - finish this list

TODO - clean up inconsistency and hypocrisy when this thing starts to actually take form :-)


## Component setup workflow

* Make an HTML "mockup" page
* Load the library scripts in your page
* Load your application script(s) in your page 
(assuming your scripting is not in the page itself - not recommended)
* Call gt.start() with a parameter object.
Pass a single object to allow future optional parameters.
Also, Javascript object literals do a fine job of emulating named parameters in other languages.
  * Configuration property value object - TBD (e.g. - enable/disable event debug tracing)
  * Controller interface object -
  an object to map controller names to implementing functions.  
  Signature and operation of such functions to be discussed below.

## Controller function operation

Controller functions are called by Gator when there is an event 
related to the portion of the page which the controller is responsible.  
The controller receives a state object (a data model, plus other items TBD) and the event.  
The controller can return null/undefined, 
in which case Gator will process the event.  
Or, the controller can return a (new?) state object, 
in which case Gator will assume that the controller has dealt with the event.
Also, the controller can return a list consisting of
a state object, or not (delegating handling of the original event), 
and one or more events to be processed by Gator 
(which then may or may not be delegated to other controllers).

Yes, that's a bit abstract.  TBD - a few concrete examples.
