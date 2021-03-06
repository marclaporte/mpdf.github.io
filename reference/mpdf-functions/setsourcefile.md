---
layout: page
title: SetSourceFile()
parent_title: mPDF functions
permalink: /reference/mpdf-functions/setsourcefile.html
modification_time: 2015-08-05T12:01:08+00:00
---

(mPDF &gt;= 2.3)

SetSourceFile – Specify the source PDF file used to import pages into the document

# Description

int <b>SetSourceFile</b> ( string <span class="parameter">$file</span> )

Specify the source PDF file used to import pages into the document.

# Parameters

<span class="parameter">file</span>

This parameter specifies the source PDF file used to import pages into the document. <b>Note:&nbsp; <span class="parameter">file</span> should be a relative path to a local file.</b>

# Return Value

<b>SetSourceFile()</b> returns the number of pages in the source file.

# Changelog

<table class="table"> <thead>
<tr> <th>Version</th><th>Description</th> </tr>
</thead> <tbody>
<tr>
<td>2.3</td>
<td>Function was added.</td>
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

$mpdf->SetImportUse(); 

$pagecount = $mpdf->SetSourceFile('logoheader.pdf');

// Import the last page of the source PDF file

$tplId = $mpdf->ImportPage($pagecount);

$mpdf->UseTemplate($tplId);

$mpdf->WriteHTML('Hallo World');

$mpdf->Output();

?>
{% endhighlight %}

# See Also

<ul>
<li><a href="{{ "/reference/mpdf-functions/setimportuse.html" | prepend: site.baseurl }}">SetImportUse()</a> - Enable the use of imported PDF files or templates</li>
<li><a href="{{ "/reference/mpdf-functions/thumbnail.html" | prepend: site.baseurl }}">Thumbnail()</a> - Print thumbnails of an external PDF file</li>
<li><a href="{{ "/reference/mpdf-functions/importpage.html" | prepend: site.baseurl }}">ImportPage()</a> - Import a page from an external PDF file</li>
<li><a href="{{ "/reference/mpdf-functions/usetemplate.html" | prepend: site.baseurl }}">UseTemplate()</a> - Insert an imported page from an external PDF file</li>
<li><a href="{{ "/reference/mpdf-functions/setpagetemplate.html" | prepend: site.baseurl }}">SetPageTemplate()</a> - Specify a page from an external PDF file to use as a template</li>
<li><a href="{{ "/reference/mpdf-functions/setdoctemplate.html" | prepend: site.baseurl }}">SetDocTemplate()</a> - Specify an external PDF file to use as a template</li>
</ul>
