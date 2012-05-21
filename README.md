#Super Basic Sass Library


Starter kit for building -fluid- grids with Sass.  Inspired by 960.gs and a plane ride to Oregon.

##Basic usage

I'm just starting to get my head around what this means for fluid layouts, so please bear with me if you find something glaringly wrong in the documentation with regards to how this thing interacts with itself. ->

This library can be used to build fixed grids like the 960.gs with no problem.  

Set the $width variable at the top of the lib.sass sheet to whatever, say 960px, chose how many columns and how wide the gutters and you're good to go.  

About a month after starting this and really starting to love fluid grids, it turns out that it's even better for those.  Set width to 100%, set your gutters to a percentage as well, and you're off to the races.

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
        
##fixed grid nesting

I have $alpha and $omega parameters for the grid() mixin.  They are set to false by default.  Set these to true to emulate the `.alpha` and `.omega` classes of the 960.gs.

###Two columns nested inside of a grid(6) column.

    #nested-left
      @include grid(3, $alpha: true)
      
    #nested-right
      @include grid(3, $omega: true)
      
##fluid grid nesting

Don't even try it.  I have no idea how this works out, since fluid columns are a percentage, and nested percentages are relative to the containing unit, and not the `$width` variable.

##Mobile

I've included very rudimentary mobile support on grid columns.  Media queries are included on the grid() mixin, so anything that is mobile sized will automatically trigger a full width an no floats.  

##Cont.

Prefix and Suffix mixins are included to pad elements in grid units.  I think I took that terminology from Blueprint, I can't remember.  Haven't yet factored those into the media queries.

    #main
      @include container
      
    #left
      @include grid(2)
      @prefix(2)
    
    #center
      @include grid(6)
      @include prefix(1)
      @include suffix(1)
      
    #right
      @include grid(4)


Push and Pull mixins are included for content first layouts:

    #main
      @include grid(12)
      @include push(4)
        
    #left-sidebar
      @include grid(4)
      @include pull(12)
        
I know this particular wheel has been invented (Compass, et al), but I get tired of unzipping a copy of the 960.gs every time I start a new project and Compass seemed to have a tiny learning curve that I didn't have time for when I wrote this.  This will at the very least cause me, and only me, to think more carefully about the semantics of my markup.

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
        

Lots of support for cross-browser gradients (in browsers that can do gradients).