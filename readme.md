# CSS Grid Course by Wes Bos

*Please check it out at [CSSGrid.io](https://CSSGrid.io).*

Here I will jot down all the elements from this course that I find note-worthy or that are new to me.

1. We need to `display: grid;` our container element in order to use this property on its items (rows + columns = *tracks*). Afterwards we can define it as an actual grid by defining the rest of the elements in CSS. Some of these elements are:
    * `grid-template-columns`: we define the width of each column (e.g. 100px 150px means we want 2 columns, with these widths respectively). We can also give the value `auto` which makes the column width responsive based on the screen size, or use functions like `repeat(4,100px)` which creates 4 columns of 100px each. *Note: You can use `px` or `rem` etc, and you can also use percentages, but they're a different story in this context.*
    * `grid-template-rows`: we define the height of each row, in a similar way.
    * `grid-gap`: we define the space we want the grid elements to have between each other (both vertically and horizontally)