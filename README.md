# hex2rgb.liquid

I needed to convert the colors values from the color picker in the theme settings form.  So I made this quick hex2rgb liquid.

I couldn't find a quick solution for this that wouldn't require javascript.  I wanted something I could just use in a css liquid.  The advantage of css rgb colors is that you can add transparency.  This is useful if you want to make the background of an element transparent without applying that transparency to all the child elements.

I hope someone finds this useful.

> I'm sure the gods of Shopify can probably tweak this to be less code, 
>but this works for me.  It would be great if we could just shove this 
>into a filter.

### Usage:

    {% comment %}
        Assign a variable called "hex2rgb_hex" to the color you want to 
        convert.This is where you'd put the variable assignment from 
        settings.
    {% endcomment %}
    {% assign hex2rgb_hex = settings.my_hex_color_var %}
    {% include 'hex2rgb' %}
    {% comment %}
        hex2rgb.liquid will return three variables hex2rgb_r, hex2rgb_g, 
        hex2rgb_b that you can apply these variables in your css rules.
        
        Note: Some other variables are also set, so beware of that.  All 
        variables are prefixed with "hex2rgb_" to try to avoid naming 
        conflicts.
    {% endcomment %}
    .my_element {
        background: rgb({{ hex2rgb_r }}, {{ hex2rgb_g }}, {{ hex2rgb_b }}, {{ settings.my_opacity_var }});
    }
