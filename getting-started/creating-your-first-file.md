---
layout: page
title: Creating your first file
parent_title: Getting Started
permalink: /getting-started/creating-your-first-file.html
modification_time: 2015-08-05T11:59:25+00:00
---

# Getting started

The following PHP will produce the most basic example with mPDF.

Include the main file containing the mpdf class:

{% highlight php %}
include('../mpdf.php');
{% endhighlight %}

Create an instance of the class:

{% highlight php %}
<?php

$mpdf=new mPDF();
{% endhighlight %}

Write some HTML code:

{% highlight php %}
<?php

$mpdf->WriteHTML('
Hallo World
');
{% endhighlight %}

Output a PDF file:

{% highlight php %}
<?php

$mpdf->Output();

exit;
{% endhighlight %}

# Notes

<div class="alert alert-info" role="alert"><strong>Note:</strong> <span class="smallblock">_MPDF_PATH</span> was required to be defined explicitly prior to mPDF 4.0 e.g. <code>define('_MPDF_PATH','../')</code>. From mPDF 4.0 the value should be automatically defined by the script itself when including the mpdf.php file.</div>

For details and options for the Output command, see&nbsp;<a href="{{ "/reference/mpdf-functions/output.html" | prepend: site.baseurl }}">Output()</a>

