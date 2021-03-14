# CSS Grid Course by Wes Bos

*Please check it out at [CSSGrid.io](https://CSSGrid.io).*

Here I will jot down all the elements from this course that I find note-worthy or that are new to me.

1. We need to `display: grid;` our container element in order to use this property on its items (rows + columns = *tracks*). Afterwards we can define it as an actual grid by defining the rest of the elements in CSS. Some of these elements are:
    * `grid-template-columns`: we define the width of each column (e.g. 100px 150px means we want 2 columns, with these widths respectively). We can also give the value `auto` which makes the column width responsive based on the screen size, or use functions like `repeat(4,100px)` which creates 4 columns of 100px each. *Note: You can use `px` or `rem` etc, and you can also use percentages, but they're a different story in this context.*
    * `grid-template-rows`: we define the height of each row, in a similar way.
    * `grid-gap`: we define the space we want the grid elements to have between each other (both vertically and horizontally)
2. Tracks are named not by the number of the column/row but by the number of lines defining them (edges), like so:
    ```
    1   2   3
    | x | y |
    ```
    *We have 2 columns but 3 tracks.*

    [This image](https://github.com/ZapDos7/css-grid/blob/master/04%20-%20CSS%20Grid%20Dev%20Tools/Line%20Meanings.png) is quite helpful for the display of tracks in Firefox.
3. Explicit VS Implicit: We define the columns explicitly, therefore the rows are defined implicitly. We use these fields:
   * `grid-auto-rows`: we give the value for the implicitly added rows
   * `grid-auto-columns`: we give the value for the implicitly added columns
   *If we give more than 1 values to these, Chrome can handle them as expected.*
4. `grid-auto-flow`: it manages the way implicitly tracks are added. Its default value is `row` which means we add the overflowing element in a new row. If we give it the value `column`, they're added in a new column (left to right by default, albeit it not being the only way)
5. Using percentages in the `grid-template-columns` field **does not** take the `grid-gap` value into consideration, which can lead to unorthodox situations and sideways scrolling (if the percentages add up to 100 but the grid gap is not 0), a commonly undesirable feature. The preferable alternative is the `fr unit` which automatically calculates the leftover space and assigns it to an element e.g.:
   a.`grid-template-columns: 200px 1fr;` means we have a column with 200px width and the other column takes over the rest space in the container.
   b. `grid-template-columns: 2fr 1fr;` means we have 2 columns, the first takes over twice the space the second one does, both sharing the space of the container in this ratio.
   c. `grid-template-columns: auto 1fr;` means we have 2 columns, the first takes over the space of the content of this element, and the other column fills up the space of the container.
6. The `repeat()` function can also take parameters like so: `3, 1fr 2fr` which means 3 repetitions of 2 tracks of which the first has half the width of the second and they both fill up the space given by the container.
7. Sizing Items:
Keep in mind that, when using `fr`, firstly we allocate the needed space (e.g. hardcoded width or content width) and then CSS automatically allocates the left over free space to the rest `fr`'d elements. 
We can therefore use the value `span X` for `grid-column` with X being an integer that specifies the span of the  element (e.g. `span 2` would mean that this element will have double the span of other elements).
Also, `grid-column` is a shortcut for these two fields: `grid-column-start` and `grid-column-end` so, for example, `grid-column: span 2;` is actually `grid-column-start: span 2; grid-column-end: auto;`
Additionally, we may define these fields by the starting and ending track number, for example: `grid-column-start: 2; grid-column-end: 5;` begins the element on the second track and spans it until track #5. A shurtcut to this is: `grid-column: 2 / 5;`. Furthermore, we can define it using `span int` for the `start` or the `end` values.
One useful tip: if we define `grid-column: 1 / -1;` we say we want the element to begin at the first track and end at the last one (useful for an unknown amount of tracks when we want the element to span with the maximum width).
All of these work with rows, similarly, with the exception of `grid-row: 1 / -1;`, which reaches the bottom **of the explicit grid** and not that of the screen.
*In order for an element to take over the space of the entire (explicit) grid, we define both `grid-row` and `grid-column` with `1 / -1`. The rest of the elements follow in the implicit grid space.*