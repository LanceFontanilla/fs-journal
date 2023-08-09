# CSS

Day 2 notes

* {
    is for all everything on page
}

body {
 for all stuff in body   
 always has a margin make it to 0
 margin:0
}

.d-flex,
.row{
display:flex
}

you can combine styles that are named differently but do the same thing with a comma

width 50% = 50% of content available

100vw = 100% of view width (not recommended to use)

width: calc (100% -5px)

can calculate the exact width minus padding to line things up correctly

padding fills up content in the box

margin separates sibling boxes and moves them away from each other


padding 1em  = just one value applies to all sides
padding 2 em 1 em  = 2 values first is top/bottom, second is left/right

usually at top
:root{ 
    --dark: Black
    --light: White
}
makes variables to use for theme of webpage to use

background-color : var(--light)

will only apply class until max width is reached
@media (max-width:600px){
.d flex {
    flex-direction: column;
}
}

Day 3 notes

Bootstrap

make sure when using bootstrap to have your stylesheet link after the bootstrap link

in developer tools, sources show all things for the project


To start with the bootstrap grid, you need a container

container has margins

container-fluid goes to the edges

section = rows

div = column

rows are broken into 12 segments

using col, col's will evenly distribute through row

cols can be given exact size to fit

cols over 12 segments will wrap to next line

you should always have a base col size with no infix 

justify only works on what is dflexed ie. rows

unsplash.com free pics 

start and end in bootstrap no left and right

img-fluid fixes image to fit in container

py is pt and pb combined

px is ps and pe combined

col 12 col-md-6
means when screen size is md to big col 6 is active
when it is smaller than med col 6 is turned off and then col 12 is active

reordering with bootstrap, put it in the col
order-first
order-last
order 0-5



