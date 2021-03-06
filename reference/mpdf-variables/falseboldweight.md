---
layout: page
title: falseBoldWeight
parent_title: mPDF Variables
permalink: /reference/mpdf-variables/falseboldweight.html
modification_time: 2015-08-05T12:01:56+00:00
---

(mPDF &gt;= 4.2)

falseBoldWeight – Specify weight used for bold text when using an artificial (outline) bold

# Description

void <b>falseBoldWeight</b>

Specify weight used for bold text when using an artificial (outline) bold. If bold text is set by &lt;b&gt; and the current font does not have a font file for the bold variant, an artificial bold is created by stroking the outline of the characters. This variable sets the width of the line and thus the "weight" of the bold text. Values between 0 and 10 are recommended.

# Values

<span class="parameter">falseBoldWeight</span><span class="smallblock"></span>

<b>Values</b>

<span class="smallblock">INTEGER </span>: set weight of bold text

<span class="smallblock"></span><span class="smallblock">DEFAULT</span>: 5

# Changelog

<table class="table"> <thead>
<tr> <th>Version</th><th>Description</th> </tr>
</thead> <tbody>
<tr>
<td>4.2</td>
<td>Variable was added.</td>
</tr>
</tbody> </table>

# Examples

{% highlight php %}
Example #1

{% endhighlight %}

{% highlight php %}
<?php

include("../mpdf.php");

$mpdf=new mPDF();

$mpdf->falseBoldWeight = 8;

$mpdf->WriteHTML('<p style="font-family: mysimplefont"><b>Hallo World</b><p>');

$mpdf->Output();

?>
{% endhighlight %}

<div class="alert alert-info" role="alert"><strong>Note:</strong> False bold text has the same character widths as the normal text.</div>

