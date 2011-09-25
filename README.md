Super Basic Sass Library
========================

Starter kit for building fluid grids with Sass.  Inspired by 960.gs and a plane ride to Oregon.

Basic usage
-----------

This library can be used to build fixed grids like the 960.gs with no problem.  Set the $width variable at the top of the lib.sass sheet to whatever, say 960px, and you're good to go.  About a month after starting this and discovering fluid grids, it turns out that it's even better for those.  Set width to 100%, set your gutters to a percentage as well, and you're off to the races.

At the top of your style sheet:

    @import lib

then something like this for your layout --

    #wrapper
      @include container()
        
    #header
      @include grid(16)
        
    #left-sidebar
      @include grid(4)
        
    #main
      @include grid(12)
        
Note that the 960.gs conventions of Alpha and Omega for nested grid units are not longer present.  I've instead included arguments for the left and right margins of a column.  If you're nesting grid units inside of others, just set the $margin-left to 0 for the first one:

    #nested-left
      @include grid(3, $margin-left:0)
      
    #nested-right
      @include grid(3, $margin-right:0)
        
This also handily negates the need for the prefix and suffix classes for moving stuff in a little more.  Instead of having to apply `grid_4 prefix_1 suffix_1` to pad a 6 grid box correctly, you just say

    @include grid(6, $margin-left: 10%, $margin-right: 10%)
    
I know suffix and prefix work with padding instead of margins, so I'll get around to that soon.

Push and Pull mixins are included for content first layouts:

    #main
      @include grid(12)
      @include push(4)
        
    #left-sidebar
      @include grid(4)
      @include pull(12)
        
I know this particular wheel has been invented (Compass, et al), but I get tired of unzipping a copy of the 960.gs every time I start a new project and Compass seemed to have a tiny learning curve that I didn't have time for when I wrote this.  This also prevents the psuedo-problem of purists looking at your markup and seeing that you don't give one single rip about putting a bunch of non-semantic classes all over the place just to achieve your layout (if you worry about that).

Styling
-------

For adding things like gradients and radiused corners:

    .button
      @include radius(3px)
      @include gradient(#f4f4f4, #ddd)
      &:hover
        @include shadow(0, 0, 2px, #444)
      &:active
        position: relative
        top: 1px
        
More to come?
-------------