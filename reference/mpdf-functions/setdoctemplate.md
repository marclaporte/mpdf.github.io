---
layout: page
title: SetDocTemplate()
parent_title: mPDF functions
permalink: /reference/mpdf-functions/setdoctemplate.html
modification_time: 2015-08-05T12:01:00+00:00
---

(mPDF &gt;= 2.3)

SetDocTemplate – Specify an external PDF file to use as a template

# Description

void <b>SetDocTemplate</b> ( [ string <span class="parameter">$file</span> [, boolean <span class="parameter">$continue</span> ]])

Specify an external PDF file to use as a template. Each page of the external source PDF file will be used as a template for the corresponding page in your new document. If the current mPDF document has more pages than the external PDF source document, the last page will (optionally) continue to be used for any remaining pages.

# Parameters

<span class="parameter">file</span>

This parameter specifies the source PDF file used as the template document.&nbsp; <span class="parameter">file</span> should be a relative path to a local file.

<span class="smallblock">DEFAULT</span>: <span class="smallblock">BLANK</span>

<span class="parameter">continue</span> = 1|0|<span class="smallblock">TRUE</span>|<span class="smallblock">FALSE</span>

If <span class="smallblock">TRUE</span> (or any positive value) it forces the last page of the source file to continue to be used as a template, if the current mPDF document contains more pages than the source file.

<span class="smallblock">DEFAULT</span>: <span class="smallblock">FALSE</span>

<div class="alert alert-info" role="alert"><strong>Note:</strong> If you want to turn the template off, just use <code>$mpdf-&gt;SetDocTemplate()</code> with no parameters.</div>

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

$mpdf->SetDocTemplate('logoheader.pdf',true); 

// Do not add page until doc template set, as it is inserted at the start of each page

$mpdf->AddPage();

$mpdf->WriteHTML('Hallo World');

// Subsequent pages from logoheader.pdf will be inserted on all subsequent pages

$mpdf->Output();

?>
{% endhighlight %}

# See Also

<ul>
<li><a href="{{ "/reference/mpdf-functions/setimportuse.html" | prepend: site.baseurl }}">SetImportUse()</a> - Enable the use of imported PDF files or templates</li>
<li><a href="{{ "/reference/mpdf-functions/restartdoctemplate.html" | prepend: site.baseurl }}">RestartDocTemplate()</a> - Re-start the use of a Document template from the next page</li>
<li><a href="{{ "/reference/mpdf-functions/thumbnail.html" | prepend: site.baseurl }}">Thumbnail()</a> - Print thumbnails of an external PDF file

</li>
<li><a href="{{ "/reference/mpdf-functions/setsourcefile.html" | prepend: site.baseurl }}">SetSourceFile()</a> - Specify the source PDF file used to import pages into the document

</li>
<li><a href="{{ "/reference/mpdf-functions/usetemplate.html" | prepend: site.baseurl }}">UseTemplate()</a> - Insert an imported page from an external PDF file</li>
<li><a href="{{ "/reference/mpdf-functions/setpagetemplate.html" | prepend: site.baseurl }}">SetPageTemplate()</a> - Specify a page from an external PDF file to use as a template

</li>
</ul>

