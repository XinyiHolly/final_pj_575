## d3.legend 

d3.legend is a quick hack to add a legend to a `d3` chart.  Simply add a `g` and `.call(d3.legend)`.  Any elements that have a title set in the `"data-legend"` attribute will be included when `d3.legend` is called.  Each title will appear only once (even when multiple items define the same data-legend) as the process uses a set based on a existing names, not an array of all items.

### Color
By default the color in the legend will try to match the fill attribute or the stroke attribute of the relevant items.  Color can be explicitly defined by attribute `"data-legend-color"`

### Order
The order of items in the legend will be sorted using the top of the bounding box for each included item.  The order can be explicitly defined by attribute `"data-legend-pos"`

### Padding
Padding will be determined by attribute `"data-style-padding"` on the legend element.
Defaults to  5.

### Size
Size of the box is determined by font size, as items are placed using `"em"` and the frame around the items is based on the bounding box.

### This Example
This example takes an existing Gist and adds a legend by defining data-legend for each series and calling `d3.legend` on a `"g"` element.   To show the font-adjustment I change font-size after one second and call `d3.legend` again.


## d3.legend 

d3.legend is a quick hack to add a legend to a `d3.graph`.  Simply add a `g` and `.call(d3.legend)`.  Any elements that has a title set in the `"data-legend"` attribute set will be included, when `d3.legend` is called.  Each title  will appear only once as the process uses a set based on a existing names, not an array of all items.

### Color
By default the color in the legend will try to match the fill attribute or the stroke attribute of the relevant items.  Color can be explicitly defined by attribute `"data-legend-color"`

### Order
The order of items in the legend will be sorted using the top of the bounding box for each included item.  The order can be explicitly defined by attribute `"data-legend-pos"`

### Padding
Padding will be determined by attribute `"data-style-padding"` on the legend element.
Defaults to  5.

### Size
Size of the box is determined by font size, as items are placed using `"em"` and the frame around the items is based on the bounding box.

### This Example
This example takes an existing Gist and adds a legend by defining data-legend for each series:
```
 .attr("data-legend",function(d) { return d.name})
```

Adding the legend is as simple as:
```javascript
legend = svg.append("g")
  .attr("class","legend")
  .attr("transform","translate(50,30)")
  .style("font-size","12px")
  .call(d3.legend)
```

To show the font-adjustment I change font-size after one second and call `d3.legend` again.

##Comments on the original gist
This line chart is constructed from a TSV file storing the daily average temperatures of New York, San Francisco and Austin over the last year. The chart employs [conventional margins](http://bl.ocks.org/3019563) and a number of D3 features:

* [d3.tsv](https://github.com/mbostock/d3/wiki/CSV) - load and parse data
* [d3.time.format](https://github.com/mbostock/d3/wiki/Time-Formatting) - parse dates
* [d3.time.scale](https://github.com/mbostock/d3/wiki/Time-Scales) - *x*-position encoding
* [d3.scale.linear](https://github.com/mbostock/d3/wiki/Quantitative-Scales) - *y*-position encoding
* [d3.scale.category10](https://github.com/mbostock/d3/wiki/Ordinal-Scales#wiki-category10), a [d3.scale.ordinal](https://github.com/mbostock/d3/wiki/Ordinal-Scales#wiki-ordinal) - color encoding
* [d3.extent](https://github.com/mbostock/d3/wiki/Arrays#wiki-d3_extent), [d3.min](https://github.com/mbostock/d3/wiki/Arrays#wiki-d3_min) and [d3.max](https://github.com/mbostock/d3/wiki/Arrays#wiki-d3_max) - compute domains
* [d3.keys](https://github.com/mbostock/d3/wiki/Arrays#wiki-d3_keys) - compute column names
* [d3.svg.axis](https://github.com/mbostock/d3/wiki/SVG-Axes) - display axes
* [d3.svg.line](https://github.com/mbostock/d3/wiki/SVG-Shapes#wiki-line) - display line shape