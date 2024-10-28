Weekly challenge to create something with D3.js to track my progress and collect resources, sometimes using an existing data viz as a source and recreating it with my own style, or creating an original data viz. Inspired by <a href="https://github.com/juanchiparra/recreating-with-d3">Juanchi Parra</a>.

| Week | Data Viz | Original or Recreation? | Source | Code | Resources |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 01 | <a href="https://littlebitsandcodes.github.io/d3-weekly/2024/01-line/">Interactive multiple lines chart (with hover tooltip)</a> | Recreation |<a href="https://www.nbcnews.com/data-graphics/labor-force-participation-pre-pandemic-levels-rcna74363">NBC News</a> | <a href="https://github.com/littlebitsandcodes/d3-weekly/tree/main/2024/01-line">2024/01</a> | <a href="https://github.com/jaredwhalen/2024-dvs-mentorship/tree/main/d3">Jared Whalen</a>, <a href="https://www.youtube.com/watch?v=g5bp02-CRAc">DataVizDad</a> (3 Parts)

## 01 - Things I Learned
- First, I used pandas in Python to clean the <a href="https://github.com/littlebitsandcodes/d3-weekly/blob/main/2024/01-line/data/fredgraph.csv">original csv file</a> downloaded from the U.S. Bureau of Labor Statistics
    - Renamed the columns (DATE -> Date, LNS11300001_NBD20200101 -> Men, LNS11300002_NBD20200101 -> Women)
    - Formatted the dates
    - Exported as json file
- 
