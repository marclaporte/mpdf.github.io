---
layout: page
title: DefHeaderByName()
parent_title: mPDF functions
permalink: /reference/mpdf-functions/defheaderbyname.html
modification_time: 2015-08-05T12:00:45+00:00
---

(mPDF &gt;= 2.0)

DefHeaderByName – Define a page header with a given name

# Description

void <b>DefHeaderByName</b> ([ string <span class="parameter">$name</span> [, array <span class="parameter">$header</span> ]])

Define a page header with a given name. Named headers can be referenced and set later in the document e.g. <a href="{{ "/reference/mpdf-functions/setheaderbyname.html" | prepend: site.baseurl }}">SetHeaderByName()</a>

<div class="alert alert-info" role="alert"><strong>Note:</strong> Do not name any header or footer starting with html_&nbsp;&nbsp; This prefix is reserved to identify an <span class="smallblock">HTML</span> header/footer when passing its name in a reference.</div>

<div class="alert alert-info" role="alert"><strong>Note:</strong> This function/method was altered in mPDF 2.2 by capitalising the first letter of the name. As function/method names in PHP have hitherto been case-insensitive, this should not cause any problems, but it is recommended where possible to use the preferred spelling.</div>

# Parameters

<span class="parameter">name</span>

User-defined name for the header. If <span class="parameter">name</span> = <span class="smallblock">BLANK</span> the name '_default' is used.<span class="smallblock">

</span>

<span class="parameter">header</span>

This parameter specifies the content of the page header as an array.

<span class="smallblock">DEFAULT</span>: array()

<b>Values</b> in the array

<span class="parameter">content</span>: <span class="smallblock">TEXT STRING</span>

<span class="parameter">font-size</span>: <span class="smallblock">FLOAT</span> font size in <b>pts</b>

<span class="parameter">font-style</span>: B|I|BI|<span class="smallblock">BLANK STRING</span>

<span class="parameter">font-family</span>: Any available font-family

<span class="parameter">color</span>: CSS '#RRGGBB' string

<span class="parameter">line</span>: 0|1 - specify whether to draw a line under the Header

{% highlight php %}
$header = array (

    'L' => array (

      'content' => '',

      'font-size' => 10,

      'font-style' => 'B',

      'font-family' => 'serif',

      'color'=>'#000000'

    ),

    'C' => array (

      'content' => '',

      'font-size' => 10,

      'font-style' => 'B',

      'font-family' => 'serif',

      'color'=>'#000000'

    ),

    'R' => array (

      'content' => 'My document',

      'font-size' => 10,

      'font-style' => 'B',

      'font-family' => 'serif',

      'color'=>'#000000'

    ),

    'line' => 1,

);
{% endhighlight %}

# Changelog

<table class="table"> <thead>
<tr> <th>Version</th><th>Description</th> </tr>
</thead> <tbody>
<tr>
<td>2.0</td>
<td>The function was added.</td>
</tr>
</tbody> </table>

# Examples

For examples and further information please see:

<ul>
<li class="manual_boxlist"><a href="{{ "/headers-footers/headers-footers.html" | prepend: site.baseurl }}">Headers &amp; Footers</a></li>
<li class="manual_boxlist"><a href="{{ "/headers-footers/method-1.html" | prepend: site.baseurl }}">Headers &amp; Footers - Method 3</a></li>
</ul>

# See Also

<ul>
<li class="manual_boxlist"><a href="{{ "/reference/mpdf-functions/deffooterbyname.html" | prepend: site.baseurl }}">DefFooterByName()</a></li>
<li class="manual_boxlist">&lt;<a href="{{ "/reference/html-control-tags/pageheader.html" | prepend: site.baseurl }}">pageheader</a>&gt;</li>
<li class="manual_boxlist"><a href="{{ "/reference/mpdf-functions/setheaderbyname.html" | prepend: site.baseurl }}">SetHeaderByName()</a></li>
<li class="manual_boxlist">&lt;<a href="{{ "/reference/html-control-tags/setpageheader.html" | prepend: site.baseurl }}">setpageheader</a>&gt;</li>
</ul>

