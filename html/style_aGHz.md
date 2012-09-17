HTML Style Guide
================

See the [W3C HTML Syntax specification](http://www.w3.org/TR/html-markup/syntax.html)
for exact definition of terms in this style guide.

Certain parts of this style guide are at odds with the [Google HTML/CSS Style Guide](http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml).
If a codebase is already following the Google style guide, new code **must** continue to follow it, incorporating as much
of this guide as possible.


Elements
--------

* Elements **must** be specified in lower case.
* Void elements **must** be closed by a space followed by `/>`.


Attributes
----------

* Attribute names **must** be specified in lower case.
* Attribute values **must** be surrounded by single quotes except when they contain a single quote,
  in which case they **may** be surrounded by double quotes. In particular, they **must not** be unqoted.
* Attribute names **must** always be associated to a value. In the case of empty attributes, the value must be `''` (e.g. `option disabled=''`).
* Attribute names and values **must** be separated exclusively by a single `=` (and _no_ spaces). E.g. `name='email' id='email_field'`.
* Attribute name/value pairs **must** be separated by either a single space or a new line. In the latter case,
  the new line **must** be indented to the position of the first attribute name in the preceding line.


Blank lines and white space
-----

* Indentation **must** _most strictly_ consist of 2 spaces. No exceptions (e.g. tabs, 4 spaces, 3 spaces).
* There **must not** be any white space at the end of any line.
  Corollary: blank lines **must** be completely empty (i.e. have a length of 0).


Must, should, may
----

> The key words **must**, **must not**, **required**, **shall**,
**shall not**, **should**, **should not**, **recommended**, **may**,
and **optional** in this document are to be interpreted as described in
[RFC 2119](http://pretty-rfc.herokuapp.com/RFC2119).

