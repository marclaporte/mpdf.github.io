---
layout: page
title: AddColumn()
parent_title: mPDF functions
permalink: /reference/mpdf-functions/addcolumn.html
modification_time: 2015-08-05T12:00:38+00:00
---

(mPDF &gt;= 2.2)

AddColumn – Start a new Column

# Description

void <b>AddColumn</b> ( )

Start a new Column in the document. Columns must be set using <a href="{{ "/reference/mpdf-functions/setcolumns.html" | prepend: site.baseurl }}">SetColumns()</a> or &lt;<a href="{{ "/reference/html-control-tags/columns.html" | prepend: site.baseurl }}">columns</a>&gt;. Height justification for the Columns is disabled when column breaks are set explicitly.

<div class="alert alert-info" role="alert"><strong>Note:</strong> Columns are incompatible with (and automatically disable): borders for block-level elements (DIV, P etc), table rotation, and collapsible margins for blocks e.g. top and bottom margins for a DIV will not collapse (default) at the top/bottom of a column.</div>

# Parameters

No parameters

# Examples

{% highlight php %}
Example #1
{% endhighlight %}

{% highlight php %}
<?php

$mpdf=new mPDF();

$mPDF->SetColumns(2);

$mpdf->WriteHTML('
Some text...
');

$mpdf->AddColumn();

$mpdf->WriteHTML('
Next column...
');

$mpdf=Output();

?>
{% endhighlight %}

# See Also

<ul>
<li class="manual_boxlist"><a href="{{ "/reference/mpdf-functions/bookmark.html" | prepend: site.baseurl }}"></a>&lt;<a href="{{ "/reference/html-control-tags/columnbreak.html" | prepend: site.baseurl }}">columnbreak</a>&gt; - HTML equivalent to AddColumn()</li>
<li class="manual_boxlist"><a href="{{ "/reference/mpdf-functions/setcolumns.html" | prepend: site.baseurl }}">SetColumns()</a> - Control the use of multiple columns on the page</li>
<li class="manual_boxlist">&lt;<a href="{{ "/reference/html-control-tags/columns.html" | prepend: site.baseurl }}">columns</a>&gt; - Control the use of multiple columns on the page</li>
</ul>
