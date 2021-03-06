---
layout: page
title: max_colH_correction
parent_title: mPDF Variables
permalink: /reference/mpdf-variables/max-colh-correction.html
modification_time: 2015-08-05T12:02:12+00:00
---

(mPDF &gt;= 1.0)

max_colH_correction – Sets maximum ratio to allow when adjusting column heights

# Description

<b>max_colH_correction</b> ( <i>1.15</i> | float )

The maximum ratio to adjust column height when justifying - too large a value can give ugly results

<div class="alert alert-info" role="alert"><strong>Note:</strong> The <span class="parameter">vAlign</span> parameter of &lt;<a href="{{ "/reference/html-control-tags/columnbreak.html" | prepend: site.baseurl }}">columnbreak</a>&gt; or <a href="{{ "/reference/mpdf-functions/setcolumns.html" | prepend: site.baseurl }}">SetColumns()</a> must be set to J or justify</div>

# Values

<table class="table"> <thead>
<tr>
<td>value</td>
<td>description</td>
</tr>
</thead> <tbody>
<tr>
<td>default

</td>
<td>1.15 

</td>
</tr>
<tr>
<td>range</td>
<td>Values above 1.0 

</td>
</tr>
</tbody> </table>

Examples

{% highlight php %}
Example #1
{% endhighlight %}

{% highlight php %}
<?php

$mpdf=new mPDF();

$mpdf->max_colH_correction = 1.3;

?>
{% endhighlight %}

