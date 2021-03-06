---
layout: page
title: autoPageBreak
parent_title: mPDF Variables
permalink: /reference/mpdf-variables/autopagebreak.html
modification_time: 2015-08-05T12:01:41+00:00
---

(mPDF &gt;= 3.1)

autoPageBreak – Specify whether to allow automatic page breaks

# Description

void <b>autoPageBreak</b>

Specify whether to allow automatic page breaks. By default, mPDF creates page breaks when required in the document. Setting the value to FALSE allows an oversized object (image etc.) to overwrite the footer and/or the bottom margin of the page.

# Values

<span class="parameter">autoPageBreak</span> =&nbsp; <span class="smallblock">TRUE </span>| <span class="smallblock">FALSE</span>

<b>Values</b>

<span class="smallblock">TRUE </span>: enables automatic page breaks

<span class="smallblock">FALSE</span>: disable automatic page breaks

<span class="smallblock">DEFAULT</span>: <span class="smallblock">TRUE</span>

# Changelog

<table class="table"> <thead>
<tr> <th>Version</th><th>Description</th> </tr>
</thead> <tbody>
<tr>
<td>3.1</td>
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

$html = '<img src="largeimage.jpg" height="290mm" /> ';

$mpdf->autoPageBreak = false;

$mpdf->AddPage();

$mpdf->WriteHTML($html);

$mpdf->Output();

?>
{% endhighlight %}

<div class="alert alert-info" role="alert"><strong>Note:</strong> This variable existed in the script before v3.1 but did not allow paging to be turned off. The variable was altered in mPDF 3.1 by making the first letter of the variable lowercase.</div>

