---
layout: page
title: tocentry
parent_title: HTML control tags
permalink: /reference/html-control-tags/tocentry.html
modification_time: 2015-08-05T12:01:30+00:00
---

(mPDF &gt;= 1.0)

tocentry – Insert an entry for the Table of Contents

# Description

&lt;<b>tocentry</b>&nbsp; <span class="parameter">content</span> [ <span class="parameter">level</span> ] [ <span class="parameter">name</span> ] /&gt;

Insert an entry for the Table of Contents referencing the current writing position in the document.

<div class="alert alert-info" role="alert"><strong>Note:</strong> The position for the Table of Contents must be specified using <a href="{{ "/reference/mpdf-functions/tocpagebreak.html" | prepend: site.baseurl }}">TOCpagebreak()</a> or &lt;<a href="{{ "/reference/html-control-tags/tocpagebreak.html" | prepend: site.baseurl }}">tocpagebreak</a>&gt; at some point before <a href="{{ "/reference/mpdf-functions/output.html" | prepend: site.baseurl }}">Output()</a> is called.</div>

<div class="alert alert-info" role="alert"><strong>Note:</strong> From mPDF 2.3 you can use more than one <acronym title="Table of Contents">ToC</acronym> in the document using the attribute <span class="parameter">name</span>.</div>

# Parameters

<span class="parameter">content</span>

This parameter sets the text as it will appear in the ToC entry. Text should be UTF-8 encoded. 

<span class="parameter">content</span> cannot contain any of the characters: &lt; &gt; &amp; ' <i>or</i> " and must use the appropriate HTML entities e.g. &lt;tocentry content="&amp;lt; 40" /&gt;

It is recommended that you use htmlspecialchars('Content', ENT_QUOTES) for this.

<span class="smallblock">REQUIRED</span>

<span class="parameter">level</span>

Specify the level of this entry (i.e. like heading 1,2,3) as a positive integer&nbsp; 

Starts at level 0

<span class="smallblock">DEFAULT</span>: 0

<span class="parameter">name</span>

Specify which <acronym title="Table of Contents">ToC</acronym> to add this entry, if using more than one <acronym title="Table of Contents">ToC</acronym> in the document. <span class="parameter">name</span> can be any alphanumeric characters (except just "0") and is case-insensitive.

<span class="smallblock">BLANK</span>&nbsp;or omitted or 0 uses the default <acronym title="Table of Contents">ToC</acronym>.

<b>Values</b> (case-insensitive)

"ALL" will add this entry to every ToC active in the document.

# Changelog

<table class="table"> <thead>
<tr> <th>Version</th><th>Description</th> </tr>
</thead> <tbody>
<tr>
<td>2.3</td>
<td><span class="parameter">name</span> attribute was added.</td>
</tr>
</tbody> </table>

# Examples

{% highlight php %}
Example #1
{% endhighlight %}

{% highlight php %}
<?php

$mpdf=new mPDF();

$mpdf->WriteHTML('Introduction');

$mpdf->WriteHTML('<tocpagebreak />');

$mpdf->WriteHTML('<tocentry content="Chapter 1" />');

$mpdf->WriteHTML('Chapter 1 ...');

$mpdf=Output();

?>
{% endhighlight %}

# Notes

<div class="alert alert-info" role="alert"><strong>Note:</strong> Since mPDF 2.0 <b>insertTOC()</b> should <b>not</b> be called at the end of the document. <a href="{{ "/reference/codepages-glyphs/iso-8859-win-comparison-chart.html" | prepend: site.baseurl }}">Output()</a> will automatically generate the ToC if it has been defined with either or <a href="{{ "/reference/mpdf-functions/tocpagebreak.html" | prepend: site.baseurl }}">TOCpagebreak()</a> or&nbsp;&lt;<a href="{{ "/reference/html-control-tags/tocpagebreak.html" | prepend: site.baseurl }}">tocpagebreak</a>&gt;.</div>

## Recommended placement

Recommended placement of ToC Entries is just after the first word following the opening tag of the block element:

{% highlight php %}
<h2>First<tocentry... /> word of a heading or block</h2>
{% endhighlight %}

or alternatively just after the opening tag of the block element:

{% highlight php %}
<h2><tocentry... />Heading or block</h2>
{% endhighlight %}

or just after a word to be marked:

{% highlight php %}
... this is a word<tocentry... /> in the middle of text to be marked ...
{% endhighlight %}

# See Also

<ul>
<li class="manual_boxlist"> <a href="{{ "/reference/mpdf-functions/tocpagebreak.html" | prepend: site.baseurl }}">TOCpagebreak()</a> - Insert a Table of Contents in the document </li>
<li class="manual_boxlist"> &lt;<a href="{{ "/reference/html-control-tags/tocpagebreak.html" | prepend: site.baseurl }}">tocpagebreak</a>&gt; - Insert a Table of Contents in the document </li>
<li class="manual_boxlist"> <a href="{{ "/reference/mpdf-functions/toc-entry.html" | prepend: site.baseurl }}">TOC_Entry()</a> - Mark a ToC entry in the document </li>
</ul>
