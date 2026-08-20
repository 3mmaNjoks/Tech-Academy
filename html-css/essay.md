CSS Grid

CSS Grid is a two-dimensional layout system that controls rows and columns at once from a single parent element. The Grid Layout Module lets developers build complex, responsive layouts without relying on float or positioning. A grid is created by setting display: grid on a parent element, which becomes the grid container and direct children automatically become grid items.

An example of using CSS grid:
.container {
  display: grid;
  grid-template-columns: 1fr 2fr 1fr;
  grid-template-rows: auto 200px auto;
  gap: 16px;
}

grid-template-columns and grid-template-rows define the number and size of tracks. The fr unit represents a fraction of the available space, so 1fr 2fr 1fr splits the row into three columns where the middle one is twice as wide as the others. "gap" (or row-gap / column-gap individually) sets spacing between cells natively, without using margin.

Grid also supports named regions through grid-template-areas, which makes a layout's structure readable directly in the CSS:
.layout {
  display: grid;
  grid-template-areas:
    "header header"
    "sidebar content"
    "footer footer";
  grid-template-columns: 200px 1fr;
}
.header  { grid-area: header; }
.sidebar { grid-area: sidebar; }
.content { grid-area: content; }
.footer  { grid-area: footer; }

Modern websites need to work on different screen sizes, including desktop computers, tablets, and smartphones. CSS Grid provides features such as repeat(), minmax(), and fractional units that can make layouts more adaptable. For example, grid-template-columns: repeat(3, 1fr) can create three equal columns, while repeat(auto-fit, minmax(220px, 1fr)) can allow columns to adapt to the available screen width. This makes Grid particularly useful for modern responsive web design.


CSS Float

Float is a one-dimensional, older technique. It places an element to the left or right of its container and lets text or inline content wrap around it. Its original purpose was wrapping text around an image, the way a newspaper column wraps around a photograph. It is implemented as:

img {
  float: left;   /* or right */
  margin-right: 16px;
}

float accepts four values: left, right, none (the default, no floating), and inherit (takes the parent's float value). This remains a legitimate, still-used case: an image floats left or right, body text flows around it.

Before Grid and Flexbox existed, floats were repurposed for full multi-column page layouts:

.col-left  { float: left; width: 30%; }
.col-right { float: left; width: 70%; }

clear: left / right / both forces an element to move below any floats on the specified side(s) rather than sitting beside them. There is no native gutter support, no automatic equal-height columns, and reordering content usually means restructuring the HTML itself.

 The core distinction is dimensionality. Float operates in one dimension and was bent into two-dimensional layouts through workarounds like clearfix and percentage widths. Grid was built for two dimensions from the start, with native gaps, alignment, and named regions. Float still has universal, decades-old browser support and remains the right tool for wrapping text around media. Modern layout systems such as Grid and Flexbox have largely replaced floats for constructing general webpage layouts, particularly when older browser compatibility is not a requirement.