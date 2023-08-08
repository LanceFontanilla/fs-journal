# CSS

* {
    is for all everything on page
}

body {
 for all stuff in body   
 always has a margin/to make it 0
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
