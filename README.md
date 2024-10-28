Weekly challenge to create something with D3.js to track my progress and collect resources, sometimes using an existing data viz as a source and recreating it with my own style, or creating an original data viz. Inspired by <a href="https://github.com/juanchiparra/recreating-with-d3">Juanchi Parra</a>.

| Week | Data Viz | Original or Recreation? | Source | Code | Resources |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 01 | <a href="https://littlebitsandcodes.github.io/d3-weekly/2024/01-line/">Interactive multiple lines chart (with hover tooltip)</a> | Recreation |<a href="https://www.nbcnews.com/data-graphics/labor-force-participation-pre-pandemic-levels-rcna74363">NBC News</a> | <a href="https://github.com/littlebitsandcodes/d3-weekly/tree/main/2024/01-line">2024/01</a> | <a href="https://github.com/jaredwhalen/2024-dvs-mentorship/tree/main/d3">Jared Whalen</a>, <a href="https://www.youtube.com/watch?v=g5bp02-CRAc">DataVizDad</a> (3 Parts)

## 01 - Process & Learnings
Data Preprocessing (Python)
- First, I used pandas in Python to clean the <a href="https://github.com/littlebitsandcodes/d3-weekly/blob/main/2024/01-line/data/fredgraph.csv">original csv file</a> downloaded from the U.S. Bureau of Labor Statistics
  - Renamed the columns:
    - `DATE` -> `Date`
    - `LNS11300001_NBD20200101` -> `Men`
    - `LNS11300002_NBD20200101` -> `Women`
  - Formatted datetime objects
  - Exported to JSON format for D3.js
 
D3.js Implementation
- I realized there are steps that have to go INSIDE the d3 data loading function (`d3.json().then()`)
  - Date parsing: convert string to Javascript Date Object by using `d => new Date(d.Date)`
  - Scale domain:
    - In this specific data viz, I manually set the y domain to have a minimum of 94
    - To set the maximum, I directly referenced the columns: `y.domain([ 94, d3.max(data, d => Math.max(d.Men, d.Women)) ]);`
    - In this case there is more than one category, so I used `Math.max(d.Men, d.Women` which compares the two values and returns the larger one
    - Another method to set the maximum by using the categories array: `y.domain([ 94, d3.max(data, d => Math.max(...categories.map(c => d[c.name]))) ]);`
- Line generator syntax varies based on dataset structure:
  - JSON, where each row has all categories as columns: `.attr("d", line.y(d => y(d[category.name])))`
  - CSV, where each category has its own array of values: `.attr("d", (d) => line(d.values))`
- Create tooltip div class outside of the d3 data loading function, otherwise it didn't work
- I later took the ticks out, but when making axes with ticks, you have to indent the ticks function so that it is chained to the axis generator `.call(d3.axisLeft(y)` and not to the selection `svg.append("g")`
