---
id: 587d7fa9367417b2b2512bce
title: Koordinaten für jeden Balken dynamisch festlegen
challengeType: 6
forumTopicId: 301487
dashedName: dynamically-set-the-coordinates-for-each-bar
---

# --description--

The last challenge created and appended a rectangle to the `svg` element for each point in `dataset` to represent a bar. Unfortunately, they were all stacked on top of each other.

The placement of a rectangle is handled by the `x` and `y` attributes. They tell D3 where to start drawing the shape in the `svg` area. The last challenge set them each to 0, so every bar was placed in the upper-left corner.

For a bar chart, all of the bars should sit on the same vertical level, which means the `y` value stays the same (at 0) for all bars. The `x` value, however, needs to change as you add new bars. Remember that larger `x` values push items farther to the right. As you go through the array elements in `dataset`, the `x` value should increase.

The `attr()` method in D3 accepts a callback function to dynamically set that attribute. The callback function takes two arguments, one for the data point itself (usually `d`) and one for the index of the data point in the array. Das zweite Argument für den Index ist optional. Here's the format:

```js
selection.attr("property", (d, i) => {

})
```

It's important to note that you do NOT need to write a `for` loop or use `forEach()` to iterate over the items in the data set. Recall that the `data()` method parses the data set, and any method that's chained after `data()` is run once for each item in the data set.

# --instructions--

Change the `x` attribute callback function so it returns the index times 30.

**Note:** Each bar has a width of 25, so increasing each `x` value by 30 adds some space between the bars. Any value greater than 25 would work in this example.

# --hints--

The first `rect` should have an `x` value of `0`.

```js
assert($('rect').eq(0).attr('x') == '0');
```

The second `rect` should have an `x` value of `30`.

```js
assert($('rect').eq(1).attr('x') == '30');
```

The third `rect` should have an `x` value of `60`.

```js
assert($('rect').eq(2).attr('x') == '60');
```

The fourth `rect` should have an `x` value of `90`.

```js
assert($('rect').eq(3).attr('x') == '90');
```

The fifth `rect` should have an `x` value of `120`.

```js
assert($('rect').eq(4).attr('x') == '120');
```

The sixth `rect` should have an `x` value of `150`.

```js
assert($('rect').eq(5).attr('x') == '150');
```

The seventh `rect` should have an `x` value of `180`.

```js
assert($('rect').eq(6).attr('x') == '180');
```

The eighth `rect` should have an `x` value of `210`.

```js
assert($('rect').eq(7).attr('x') == '210');
```

The ninth `rect` should have an `x` value of `240`.

```js
assert($('rect').eq(8).attr('x') == '240');
```

# --seed--

## --seed-contents--

```html
<body>
  <script>
    const dataset = [12, 31, 22, 17, 25, 18, 29, 14, 9];

    const w = 500;
    const h = 100;

    const svg = d3.select("body")
                  .append("svg")
                  .attr("width", w)
                  .attr("height", h);

    svg.selectAll("rect")
       .data(dataset)
       .enter()
       .append("rect")
       .attr("x", (d, i) => {
         // Add your code below this line



         // Add your code above this line
       })
       .attr("y", 0)
       .attr("width", 25)
       .attr("height", 100);
  </script>
</body>
```

# --solutions--

```html
<body>
  <script>
    const dataset = [12, 31, 22, 17, 25, 18, 29, 14, 9];

    const w = 500;
    const h = 100;

    const svg = d3.select("body")
                  .append("svg")
                  .attr("width", w)
                  .attr("height", h);

    svg.selectAll("rect")
       .data(dataset)
       .enter()
       .append("rect")
       .attr("x", (d, i) => {
         return i * 30
       })
       .attr("y", 0)
       .attr("width", 25)
       .attr("height", 100);
  </script>
</body>
```
