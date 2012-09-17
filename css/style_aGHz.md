CSS Style Guide
===============

    /* Generic example of CSS style */
    
    selector[, another_selector][,
    a_really_big_selector_on_its_own_line] {
      /* element-related, starting from outermost properties
         going to innermost in terms of physical location:
         display > floating and vertical align > position > coordinates and size > margin > border > padding */
      display: block|inline|inline-block|none;
      float: ;
      vertical-align: ;
      position: ;
      left|right|top|bottom: ;
      width|height|max-width|maxheight: ;
      margin: ;
      border: ;
      padding: ;
    
      /* background-related properties such as color, image or gradients */
      background-color: ;
      background: ;
      -webkit-box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
         -moz-box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
              box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
              
      background: #48ace4; /* Old browsers */
      background:        -webkit-gradient(linear, left top, left bottom, color-stop(0%, #48ace4), color-stop(100%, #368dbe)); /* Chrome, Safari4+ */
      background:    -moz-linear-gradient(top, #48ace4 0%, #368dbe 100%); /* FF3.6+ */
      background: -webkit-linear-gradient(top, #48ace4 0%, #368dbe 100%); /* Chrome10+, Safari5.1+ */
      background:      -o-linear-gradient(top, #48ace4 0%, #368dbe 100%); /* Opera 11.10+ */
      background:     -ms-linear-gradient(top, #48ace4 0%, #368dbe 100%); /* IE10+ */
      background:         linear-gradient(to bottom, #48ace4 0%, #368dbe 100%); /* W3C */
      filter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#48ace4', endColorstr='#368dbe', GradientType=0); /* IE6-9 */
  
      /* font-related properties */
      font-family: ;
      font-style: ;
      font-weight: ;
      font-size: ;
      line-height: ;
      text-align: ;
      color: ;
      
      /* other properties */
      }
      sub_selector { /* hierarchical child of above selector */
        ...
        }
      furthermore_selector { /* narrower application of above selector */
        ...
        }


Selectors
---------
* Selectors **must** be separated exclusively by a comma followed by a single space.
* Selectors **should** in general be specified on a single line.
* Selectors **may** be split on multiple lines for logical grouping or aesthetic reasons. Do not abuse this.
* Multi-line selectors **must** break line _after_ a comma.
* Multi-line selectors **must not** be divided by blank lines. If you find you need such divisions for clarity
  purposes, you **should** rethink your CSS or DOM structure. You **may** break this rule at your own peril.


Names
-----
* Names (identifiers, class names, even field names) **should** be in lower case, with words separated by a
  single underscore.
* Words in names **shoud not** be separated by hyphens, even though this is traditional for CSS, in order to
  distinguish them from CSS properties and constants, and to enable us to pretend that we're real programmers.
* Words in names **should not** follow camelCase because it's just plain ugly.


Properties
----------
* Properties **should** be specified almost exclusively on a single line.
* Properties **may** occasionally be collapsed to a single line when only a small number describe a relatively
  insignificant selector. In such a case, the closing bracket **must** also be on the same line.
* Properties **must** appear in a consistent order: placement and dimensions, background, font and content, followed
  by miscelaneous properties.
* Placement and dimension properties **must** be ordered starting from outermost to innermost:
  display, floating and vertical align, position, coordinates and size, margin, border, padding.
* Vendor-specific properties **must** align at the colon, and vendor-specific functions **must**
  align at the opening parenthesis.

Brackets
--------

* Opening bracket **should** follow its selectors on the same line.
  In such a case, a _single_ space **must** separate the bracket from the selector
- Opening bracket **may** be on a new line by itself
  _on very rare and special occasions guided by thorough application of aesthetic judgement_.
  In such a case, opening bracket **must** be at the same indentation level as the selector it opens.
* Closing bracket **must** be on a line by itself and at the same indentation level as the rules it encloses.


Blank lines and white space
-----

* Indentation **must** _most strictly_ consist of 2 spaces. No exceptions (e.g. tabs, 4 spaces, 3 spaces).
* There **must not** be any white space at the end of any line.
  Corollary: blank lines **must** be completely empty (i.e. have a length of 0).
* Selectors hierarchically related in the DOM **must** be indented to the closing bracket of their parent.
* Selectors specifying narrower applications of an existing selector (e.g. `p` and `p.forealz`) **must**
  be indented to the closing bracket of the more general selector.
* Properties **must** be separated by blank lines as outlined above.
  Other properties **may** be ordered and separated according to aesthetic judgment.
* Loosely-related selectors **should** be separated by a single blank line.
* Completely unrelated selectors **should** be separated by two blank lines.


Must, should, may
----

> The key words **must**, **must not**, **required**, **shall**,
**shall not**, **should**, **should not**, **recommended**, **may**,
and **optional** in this document are to be interpreted as described in
[RFC 2119](http://pretty-rfc.herokuapp.com/RFC2119).

