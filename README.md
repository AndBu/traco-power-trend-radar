# Motivation

At [Traco Power](http://tracopower.com), we maintain a Trend Radar to help our stakeholders align on important trends along our value chain.
It is based on the [Zalando Tech Radar](http://zalando.github.io/tech-radar/), which itself is based on the [pioneering work by ThoughtWorks](https://www.thoughtworks.com/radar).

Our version includes changes that make working with general trends (as opposed to technology trends) easier for us:
* Additional information about each trend opens in a modal window when clicking on an entry or a blip
* An Excel file with a proof-of-concept VBA macro to export trend entries is included. The file can be used to populate the radar. It is not encouraged to rely on Excel to keep the radar up-to-date, but it makes it a lot easier to test out the radar before deploying it.
* The definition of the "triangles" is now user configurable (previously, it was hard-coded to "moved up" and "moved down")

**WARNING, this repository is not actively maintained. The code is posted here to give back to the community.**

* If the above changes **are** important to you, consider forking the repository to build on it and keep it in sync with the original [Zalando Tech Radar](http://zalando.github.io/tech-radar/) yourself.
* If the above changes **are not** important to you, we encourage you to work with the original [Zalando Tech Radar](http://zalando.github.io/tech-radar/) or another trend radar instead.

This repository contains the code to generate the visualization: [`radar.js`](/docs/radar.js) (based on [d3.js v4](https://d3js.org)). Feel free to use and adapt it for your own purposes.

## Usage

1. include `d3.js` and `radar.js`:

```html
<script src="https://d3js.org/d3.v4.min.js"></script>
<script src="path/to/repository/docs/release/traco-radar-0.7.js"></script>
```

2. insert an empty `svg` tag for the radar and an empty  `div` tag for the modal and assign the following ids:

```html
<svg id="radar"></svg>
<div id="modal"></div>
```

3. configure the radar visualization:

```js
radar_visualization({
  svg_id: "radar",
  modal_id: "modal",
  width: 1450,
  height: 1000,
  colors: {
    background: "#fff",
    grid: "#bbb",
    inactive: "#ddd"
  },
  title: "My Radar",
  quadrants: [
    { name: "Bottom Right" },
    { name: "Bottom Left" },
    { name: "Top Left" },
    { name: "Top Right" }
  ],
  rings: [
    { name: "INNER",  color: "#5ba300" },
    { name: "SECOND", color: "#009eb0" },
    { name: "THIRD",  color: "#c7ba00" },
    { name: "OUTER",  color: "#e09b96" }
  ],
  moved_up: "moved up",
  moved_down: "moved down",
  print_layout: true,
  links_in_new_tabs: true,
  entries: [
   {
      label: "Some Entry",
      quadrant: 3,          // 0,1,2,3 (counting clockwise, starting from bottom right)
      ring: 2,              // 0,1,2,3 (starting from inside)
      moved: -1             // -1 = moved out (triangle pointing down)
                            //  0 = not moved (circle)
                            //  1 = moved in  (triangle pointing up)
   },
    // ...
  ]
});
```

Entries are positioned automatically so that they don't overlap.

As a comparable working example, you can check out `docs/index.html` in the source files of the [Traco Power Trend Radar]("https://github.com/AndBu/traco-power-trend-radar")


## Local Development

1. install dependencies with yarn (or npm):

```
yarn 
```

2. start local dev server:

```
yarn start
```

3. your default browser should automatically open and show the url
 
```
http://localhost:3000/
```

## License

```
The MIT License (MIT)

Copyright (c) 2021-2023 André Buffing - Traco Electronic AG 
Copyright (c) 2017-2023 Zalando SE

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
```
