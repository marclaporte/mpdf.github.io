---
layout: page
title: jpgraph
parent_title: HTML control tags
permalink: /reference/html-control-tags/jpgraph.html
modification_time: 2015-08-05T12:01:25+00:00
---

(mPDF &gt;= 2.4)

jpgraph — Generate a graph from table data (requires <a href="http://www.aditus.nu/jpgraph/" target="_blank">JPGraph</a> integration)

# Description

&lt;<b>jpgraph</b> [ <span class="parameter">table </span>] [ <span class="parameter">type </span>] [ <span class="parameter">stacked </span>] [ <span class="parameter">dpi </span>] [ <span class="parameter">title </span>] [ <span class="parameter">splines </span>] [ <span class="parameter">bandw </span>] [ <span class="parameter">antialias </span>] [ <span class="parameter">label-y</span> ] [ <span class="parameter">label-x </span>] [ <span class="parameter">axis-x</span> ] [ <span class="parameter">axis-y</span> ] [ <span class="parameter">percent </span>] [ <span class="parameter">series </span>] [ <span class="parameter">data-col-begin</span> ] [ <span class="parameter">data-row-begin</span> ] [ <span class="parameter">data-col-end</span> ] [ <span class="parameter">data-row-end</span> ] [ <span class="parameter">show-values</span> ] [ <span class="parameter">width</span> ] [ <span class="parameter">height</span> ] [ <span class="parameter">legend-overlap</span> ] [ <span class="parameter">hide-grid</span> ] [ <span class="parameter">hide-y-axis</span> ] /&gt;

Generates and inserts a graph into the document at the current writing position. &lt;jpgraph&gt; must follow the table which it refers to (not necessarily immediately). Requires <span class="parameter">useGraphs</span> set to <span class="smallblock">TRUE</span>.

<div class="alert alert-info" role="alert"><strong>Note:</strong> This requires <a href="http://www.aditus.nu/jpgraph/" target="_blank">JPGraph</a> to be installed on the server. See <a href="{{ "/what-else-can-i-do/graphs.html" | prepend: site.baseurl }}">Graphs</a> for further information.</div>

# Attributes

<span class="parameter">table</span>

This attribute (optionally) specifies the table "id" or "name" from which to use data. 

<span class="smallblock">BLANK</span> or omitted - uses data from the most recent table (in order of the HTML code being parsed) as long as the table did not have an "id" or "name" defined.

<span class="parameter">type</span>

Specifies the type of graph.&nbsp;

<span class="smallblock">BLANK</span> or omitted uses the default value.

<b>Values</b> (case-insensitive)

bar

horiz_bar (horizontal bar graph)

line

radar

pie

pie3d

xy

scatter

<span class="smallblock">DEFAULT</span>: bar

Graphs of type xy or scatter will expect exactly two columns/rows of numerical data - giving X and Y co-ordinates respectively. In the xy graph, the x values need to be in numerical order.

<span class="parameter">stacked</span> = 1|0

Specifies whether to "stack" bars in graphs of type <i>bar</i> or <i>horizontal-bar</i>.

<span class="smallblock">BLANK</span>&nbsp;or omitted uses default value.

<span class="smallblock">DEFAULT</span>: 0 (OFF)

<span class="parameter">dpi</span>

Sets the image resolution of the graph in dots per inch (dpi). NB Large values will use extensive amounts of memory.

<span class="smallblock">BLANK</span>&nbsp;or omitted uses default value.

<b>Values</b>

<span class="smallblock">INTEGER</span>: between 50 - 2400

<span class="smallblock">DEFAULT</span>: 150

<span class="parameter">title&nbsp;</span>

Specifies a text string to use atitle for the graph

<span class="parameter">splines</span> = 1|0

Specify whether to smooth lines for <span class="parameter">xy</span>-type line graphs 

<span class="smallblock">DEFAULT</span>: 0

<span class="parameter">bandw</span> = 1|0

Specify whether to create a black and white graph

<span class="smallblock">DEFAULT</span>: 0 (colour)

<span class="parameter">antialias </span> = 1|0

Specify whether to use antialias in generating the graphs.

If antialias is used better quality curves are produced, but graph lines will only be 1px wide - which will be very thin when using higher resolutions e.g. 300dpi (this is a limitation set by JPGraph)

<span class="smallblock">DEFAULT</span>: 1 (use antialias) for all types except <span class="parameter">line</span> and <span class="parameter">radar</span>.

<span class="parameter">label-y</span>

Specifies a text string to use a label across the y-axis

<span class="parameter">label-x </span>

Specifies a text string to use a label across the x-axis

<span class="parameter">axis-x</span>

Specify the scale or type of x-axis.

<b>Values</b> (case-insensitive)

text: uses text labels for the x-axis

lin: use a linear scale

log: use a logarithmic scale

<span class="smallblock">DEFAULT</span>: text (except if splines are set when it will default to 'lin')

<span class="parameter">axis-y</span>

Specify the scale or type of y-axis.

<b>Values</b> (case-insensitive)

lin: use a linear scale for the y-axis

percent: show a percent sign on a linear scale

log: use a logarithmic scale

<span class="smallblock">DEFAULT</span>: lin

<span class="parameter">percent </span> = 1|0

Specify whether to graph the data as percentages of the series total. This useful if you have 2 series of data to compare such as the number of cycle accidents per age group compared with the population broken down by age group.

<span class="smallblock">DEFAULT</span>: 0

<span class="parameter">series </span>

Specify whether the table data has the data series in columns or rows.

<b>Values</b> (case-sensitive)

cols: data series are read from table columns

rows: data series are read from table rows

<span class="smallblock">DEFAULT</span>:cols

<span class="parameter">data-col-begin</span>

Specify the column number to start reading data

<b>Values</b>

<span class="smallblock">INTEGER</span>: 

<span class="smallblock">DEFAULT</span>: 2 (except <span class="parameter">scatter </span>and <span class="parameter">xy </span>and <span class="parameter">series</span>='cols', when = 1)

<span class="parameter">data-row-begin</span>

Specify the row number to start reading data

<b>Values</b>

<span class="smallblock"> INTEGER</span>: 

<span class="smallblock">DEFAULT</span>: 2 (except <span class="parameter">scatter </span>and <span class="parameter">xy </span>and <span class="parameter">series</span>='rows', when = 1)

<span class="parameter">data-col-end</span>

Specify the last column number to contain data.

<b>Values</b>

0: Read data up to, and including, the last column

<span class="smallblock">POSITIVE INTEGER</span>: Specify the last column by number to include data

<span class="smallblock">NEGATIVE INTEGER</span>: Specify the column reading from the last column e.g. "-2" = 2nd column from last

<span class="smallblock">DEFAULT</span>: 0

<span class="parameter">data-row-end</span>

Specify the last row number to contain data.

<b>Values</b>

0: Read data up to, and including, the last row 

<span class="smallblock">POSITIVE INTEGER</span>: Specify the last row by number to include data

<span class="smallblock">NEGATIVE INTEGER</span>: Specify the row reading from the last row e.g. "-2" = 2nd row from last

<span class="smallblock">DEFAULT</span>: 0

<span class="parameter">show-values</span> = 1|0

Specify whether to show the value for each data point

<span class="smallblock">DEFAULT</span>: 0

<span class="parameter">width

height</span>

Specify width and/or height fro the graph. If only one is specified, the graph is resized in proportion to the default sizings.

<b>Values</b>

<span class="smallblock"> </span>Any valid CSS value including 100%, 300px etc. If no units are defined, pixels are assumed.

<span class="smallblock">DEFAULT</span>: Values are set according to graph type (in graph.php)

&nbsp;&nbsp; $defsize['pie'] = array('w' =&gt; 600, 'h' =&gt; 300);

&nbsp;&nbsp; $defsize['pie3d'] = array('w' =&gt; 600, 'h' =&gt; 300);

&nbsp;&nbsp; $defsize['radar'] = array('w' =&gt; 600, 'h' =&gt; 300);

&nbsp;&nbsp; $defsize['line'] = array('w' =&gt; 600, 'h' =&gt; 400);

&nbsp;&nbsp; $defsize['xy'] = array('w' =&gt; 600, 'h' =&gt; 400);

&nbsp;&nbsp; $defsize['scatter'] = array('w' =&gt; 600, 'h' =&gt; 400);

&nbsp;&nbsp; $defsize['bar'] = array('w' =&gt; 600, 'h' =&gt; 400);

&nbsp;&nbsp; $defsize['horiz_bar'] = array('w' =&gt; 600, 'h' =&gt; 500);

<span class="parameter">legend-overlap</span> = 1|0

Specify whether to overlap the legend box over the graph (ignored for <span class="parameter">pie</span>, <span class="parameter">pie3d</span> and <span class="parameter">radar</span>)

<span class="smallblock">DEFAULT</span>: 0

<span class="parameter">hide-grid</span> = 1|0

Specify whether to hide the grid lines (ignored for <span class="parameter">pie</span>, <span class="parameter">pie3d</span> and <span class="parameter">radar</span>)

<span class="smallblock">DEFAULT</span>: 0

<span class="parameter">hide-y-axis</span> = 1|0

Specify whether to hide the whole y-axis - including the grid lines (ignored for <span class="parameter">pie</span>, <span class="parameter">pie3d</span> and <span class="parameter">radar</span>)

<span class="smallblock">DEFAULT</span>: 0

<div class="alert alert-info" role="alert"><strong>Note:</strong> Other attributes or styles supported by &lt;img&gt; can be used, except for <span class="parameter">width </span>and <span class="parameter">height </span>(which are ignored) and of course <span class="parameter">src</span>.</div>

# Changelog

<table class="table"> <thead>
<tr> <th>Version</th><th>Description</th> </tr>
</thead> <tbody>
<tr>
<td>2.4</td>
<td>The function was added.</td>
</tr>
</tbody> </table>

# Examples

{% highlight php %}
Example #1
{% endhighlight %}

{% highlight php %}
<?php

include("../mpdf.php");

define("_JPGRAPH_PATH", '../../jpgraph_5/src/'); // must define this before including mpdf.php file

define("_TTF_FONT_NORMAL", 'arial.ttf');

define("_TTF_FONT_BOLD", 'arialbd.ttf');

$mpdf=new mPDF(); 

$mpdf->useGraphs = true;

$html = '

<table id="tbl_1"><tbody>

<tr><td></td><td><b>Female</b></td><td><b>Male</b></td></tr>

<tr><td>35 - 44</td><td><b>4</b></td><td><b>2</b></td></tr>

<tr><td>45 - 54</td><td><b>5</b></td><td><b>7</b></td></tr>

<tr><td>55 - 64</td><td><b>21</b></td><td><b>18</b></td></tr>

<tr><td>65 - 74</td><td><b>11</b></td><td><b>14</b></td></tr>

<tr><td>75 - 84</td><td><b>10</b></td><td><b>10</b></td></tr>

<tr><td>85 - 94</td><td><b>2</b></td><td><b>1</b></td></tr>

<tr><td>95 - 104</td><td><b>1</b></td><td><b></b></td></tr>

<tr><td>TOTAL</td><td>54</td><td>52</td></tr>

</tbody></table>

<jpgraph table="tbl_1" type="bar" stacked="0" dpi="300" title="New subscriptions" splines="1" bandw="0" antialias="1" label-y="% patients" label-x="Age group" axis-x="text" axis-y="lin" percent="0"  series="cols" data-col-begin="2" data-row-begin="2" data-col-end="0" data-row-end="-1" show-values="1" width="600" legend-overlap="1" hide-grid="1" hide-y-axis="1" />

';

$mpdf->WriteHTML($html );

$mpdf->Output();

exit;

?>
{% endhighlight %}

# See Also

<ul>
<li class="manual_boxlist"><a href="{{ "/reference/mpdf-variables/usegraphs.html" | prepend: site.baseurl }}">useGraphs</a> - Parse table data from the HTML, and allow the use of &lt;<a href="{{ "/reference/html-control-tags/jpgraph.html" | prepend: site.baseurl }}">jpgraph</a>&gt;</li>
<li class="manual_boxlist"><a href="{{ "/what-else-can-i-do/graphs.html" | prepend: site.baseurl }}">Graphs</a> - More about JPGraph and graphs

</li>
</ul>

