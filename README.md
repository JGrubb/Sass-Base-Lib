Super Basic Sass Library
========================

Inspired by a plane ride to Oregon and the 960.gs.  

Basic usage
-----------

At the top of your style sheet:

    @import lib

then:

    #wrapper
        @include container()
        
    #header
        @include grid(16)
        
    #left-sidebar
        @include grid(4)
        
    #main
        @include grid(12)