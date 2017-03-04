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
