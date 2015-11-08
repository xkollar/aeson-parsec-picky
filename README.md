Picky JSON Parser
=================

JSON parser with nice error messages and little
more strict syntax (whitespace-wise). Based on
[Aeson](http://hackage.haskell.org/package/aeson) and
[Parsec](http://hackage.haskell.org/package/parsec).

Interacting with user
---------------------

JSON being nice readable text-based format seems good candidate
for occasionally being created by a user. While Aeson provides really
super-optimized parsers, their error messages are not very helpful.
Creating larger JSON object by hand can be frustrating (especially)
when you make even a small mistake.

While this parser is not optimized for speed, it tries to produce
nice and helpful error messages. (This library uses Parsec library.)

Another way to help your user is not allowing him or her to
learn wrong habbits. Just look at the following piece of code (be
warned - there are trailing spaces there):

~~~ .json
{ "name"   :   
   ,   

"Hal"
}
~~~

That (in my opinion) is something one would not like to see in files
users of his or hers tool produces. So why not forbid that? This
library does not allow such things while still allowing to make
the input more airy.

Composability
-------------

This library was written with re-usability in mind. Parsers it
provides do not consume any spaces before of after corresponding
values and therefore are more easily reusable for your own projects.

Parsing to Aeson data types
---------------------------

Aeson library is nice to work with with large ecosystem of useful
libraries. So why not join them and avoid reinventing the wheel?

Motivation
----------

Why another JSON parser? Internal (company I work for) tool for
testing JSON RPC used simple format that re-used JSON parsers.
It was already re-written few times, and reasons were:

* Bad error messages for people who were writing testing scripts.
* They were able to do horrible stuff (trailing spaces, ...).
* Some parsers that used Parsec (and produced helpful error messages)
  were producing non-aeson data structures and we already use
  aeson on some places so we had option to be more heterogeneous
  or make useless conversions.

No parser I was aware of seemed to solve these issues.
