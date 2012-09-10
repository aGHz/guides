CSS Style Guide
===============

    selector[, selector][,
    selector] {
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
      subselector (hierarchical child of selector above) {
        ...
        }
      alsoselector (narrower application of selector above) {
        ...
        }


Brackets
--------

* Opening bracket **should** follow its selectors on the same line.
- Opening bracket **may** be on a new line by itself on very rare and special occasions guided by thorough application of aesthetic judgement.
  It such a case, opening bracket **must** be at the same indentation level as the selector it opens.
* Closing bracket **must** be on a line by itself and at the same indentation level as the rules it encloses.      


Blank lines and white space
-----

* Indentation **must** _most strictly_ consist of 2 spaces. No exceptions (e.g. tabs, 4 spaces, 3 spaces).
* There **must not** be any white space at the end of any line.
- Corollary: blank lines **must** be completely empty (i.e. have a length of 0).
* Selectors hierarchically related in the DOM **must** be indented to the closing bracket of their parent.
* Selectors specifying narrower applications of an existing selector (e.g. `p` and `p.forealz`) **must**
  be indented to the closing bracket of the more general selector.
* Properties **must** be separated by blank lines as outlined above.
- Other properties **may** be ordered and separated according to aesthetic judgment.
* Loosely-related selectors **should** be separated by a single blank line.
* Completely unrelated selectors **should** be separated by two blank lines.


    The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL
    NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED",  "MAY", and
    "OPTIONAL" in this document are to be interpreted as described in
    RFC 2119.