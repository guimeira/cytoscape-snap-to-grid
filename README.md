cytoscape-snap-to-grid
================================================================================
![cytoscape-snap-to-grid][picture]

## Description

Adds snap-to-grid and guide lines to Cytoscape.js graphs.


## Dependencies

 * [Cytoscape.js]


## Usage instructions

Download the library:
 * via npm: `npm install cytoscape-snap-to-grid`,
 * via bower: `bower install cytoscape-snap-to-grid`, or
 * via [direct download] in the repository (probably from a tag).

`require()` the library as appropriate for your project:

CommonJS:
```js
var cytoscape = require('cytoscape');
var snap-to-grid = require('cytoscape-snap-to-grid');

snap-to-grid( cytoscape ); // register extension
```

AMD:
```js
require(['cytoscape', 'cytoscape-snap-to-grid'], function( cytoscape, snap-to-grid ){
  snap-to-grid( cytoscape ); // register extension
});
```

Plain HTML/JS has the extension registered for you automatically, because no `require()` is needed.


## API

The extension is enabled by invoking `snapToGrid` on your Cytoscape object:

```js
cy.snapToGrid();
```

Optionally, a settings object can be passed as argument. The available settings are:

* `stackOrder` (default: `-1`): Cytoscape graphs are drawn on several layers on a stack. This setting adjust the position of the grid layer on that stack. `-1` draws the grid behind everything drawn by Cytoscape and higher values bring the grid to the front. A value of `4` should be enough to draw the grid over everything drawn by Cytoscape.
* `gridSpacing` (default: `40`): distance between the lines of the grid.
* `strokeStyle` (default: `"#CCCCCC"`): determines the style of the grid lines. Any valid [CSS color value] is acceptable.
* `lineWidth` (default: `1.0`): thickness of the grid lines.
* `lineDash` (default: `[5,8]`): array of numbers that defines the style of the dash. The first number specifies the length of the first dash, the second number specifies the length of the first gap. The length of this array should be even. If it is odd, the array is copied and concatenated. Read [this] for more details. For a solid line, set this parameter to `[]`.
* `zoomDash` (default: `true`): determines whether the size of the dashes should change when the drawing is zoomed in and out.
* `panGrid` (default: `true`): determines whether the grid should move then the user moves the graph.
* `snapToGrid` (default: `true`): when enabled, centers the nodes on the nearest grid cell.
* `drawGrid` (default: `true`): enables or disables the grid drawing.

After the extension is enabled, other functions can be invoked by passing the function name as a parameter to the `snapToGrid` function. For example:
```js
cy.snapToGrid('snapOn');
```

The available functions are:
* `snapOn`: enables the snap-to-grid functionality. All the nodes currently added to the graph are moved to the center of the nearest cell.
* `snapOff`: disables the snap-to-grid functionality.
* `gridOn`: enables the grid drawing.
* `gridOff`: disables the grid drawing.
* `refresh`: forces the grid to be redrawn.
* `option`: when invoked with a single string argument, returns the current value of the option corresponding to that argument. When invoked with a string and a value, sets the value of that option. The options `drawGrid` and `snapToGrid` should be changed by the `snapOn`, `snapOff`, `gridOn` and `gridOff` methods and not by this function.


[Cytoscape.js]: http://js.cytoscape.org/
[direct download]: /tags
[CSS color value]: https://developer.mozilla.org/en-US/docs/Web/CSS/color_value
[this]: https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/setLineDash
[picture]: /snap-to-grid.png
