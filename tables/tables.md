---
layout: page
title: Tables
parent_title: Tables
permalink: /tables/tables.html
modification_time: 2015-08-05T11:59:43+00:00
---

# Styles

For a full list of CSS styles supported by mPDF for tables/cells, see&nbsp;<a href="{{ "/css-stylesheets/supported-css.html" | prepend: site.baseurl }}">Valid CSS</a>. Note the custom attribute "topntail" which I have added to add a horizontal border at the top and bottom of the table, and under the THEAD row if present.

Block-level tags (DIV, P etc) are ignored inside tables, including any CSS styles - inline CSS or stylesheet classes, id etc. To set text characteristics within a table/cell, either define the CSS for the table/cell, or use in-line tags e.g. &lt;SPAN style="..."&gt;

Both models of border-collapse are supported (CSS border-collapse:collapse or separate), as well as cellSpacing and cellPadding.

# Rotate

Tables can be rotated by 90 degrees clockwise or anticlockwise using either:

&lt;table rotate="90|-90"&gt; or

&lt;table style="rotate:90|-90;"&gt;

(90 is clockwise, and -90 is anticlockwise)

Table rotation is disabled when columns are used.

# Autosize

If a table's minimum width is too wide for the page/div/column, it will automatically reduce the font size in order to fit. The minimum width is calculated by the sum of column widths required to fit the longest single word in the column.

This function is ON by default, set in the <span class="filename">config.php</span> file as var <code>$shrink_tables_to_fit=1.4</code>

The font size will only be reduced to a minimum size to avoid ridiculous results. The value of <code>$shrink_tables_to_fit</code> is the maximum factor by which the font-size will be reduced.

If it is turned off e.g. <code>$mpdf-&gt;shrink_tables_to_fit=0;</code> it is overridden by a specific declaration for a table e.g.:

<code>&lt;table autosize="2.4"&gt;</code> or

<code>&lt;table style="autosize:2.4;"&gt;</code>

A value of 1 will prevent any (unnecessary) resizing.

# page-break-inside:avoid

If a table has the property page-break-inside:avoid and will not fit on the page, mPDF tries to shrink it to fit - up to a maximum "shrink-factor" set by the variable $mpdf-&gt;shrink_tables_to_fit - default is 1.4 (i.e. about 70% original size). If this still won't fit, it moves it to the next page.

A shrunk table may not be what you want. You can prevent this resizing either by setting the maximum shrink-factor for a particular table e.g. &lt;table autosize="1"&gt; or by setting the variable for the whole document i.e. <code>$mpdf-&gt;shrink_tables_to_fit=1;</code>

(Note that mPDF will always resize tables if it is the only way to fit a row or whole table onto a full page.)

# Repeating Table Header row on new page

If a table is split onto more than one page, the first row of the table will be repeated at the top of the new page if either:

<code>&lt;table repeat_header="1"&gt;</code> or

<code>&lt;thead&gt;</code> or <code>&lt;tfoot&gt; </code>is defined

# Error reporting

NB 2 values are defined in the <span class="filename">config.php</span> file which control error reporting for tables:

<code>$table_error_report = false;</code> // Die and report error if table is too wide to contain whole words (even after autosizing)

<code>$table_error_report_param = '';</code> // Parameter which can be passed to show in error report i.e. chapter number being processed.

