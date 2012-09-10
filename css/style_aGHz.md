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
      }
      sub- or otherwise related selector {
        ...
        }
