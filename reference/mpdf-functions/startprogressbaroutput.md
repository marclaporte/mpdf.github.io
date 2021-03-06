---
layout: page
title: StartProgressBarOutput()
parent_title: mPDF functions
permalink: /reference/mpdf-functions/startprogressbaroutput.html
modification_time: 2015-08-05T12:01:11+00:00
---

(mPDF &gt;= 4.2)

StartProgressBarOutput – Enable progress bars to be shown during file generation

# Description

void <b>StartProgressBarOutput</b> ( [ string <span class="parameter">$mode</span> ] )

Enable progress bars to be shown during file generation. Not recommended for general use, but may be helpful for development purposes, or for slow document generation. To set this value globally you can edit the value for <code>progressBar</code> in the configuration file <span class="filename">config.php</span>

<div class="alert alert-info" role="alert"><strong>Note:</strong> You may need to define the constant _MPDF_URI if you use progress bars. The constant _MPDF_URI is needed to redirect the user to the PDF file (and prior to mPDF 5.0 to locate a javascript file within the progress bar script). It must be either a relative path (e.g. '../') or a full URI (e.g. 'http://www.mydomain.com/mpdf/'). If you do not define it before calling mPDF() mPDF will assign it the same value as _MPDF_PATH. This is fine if you have used a relative path. _MPDF_PATH requires either a relative path or a filesystem real path (e.g. '/homepages/27/d84233457/htdocs/')</div>

# Parameters

<span class="parameter">mode</span>

<b>Values</b> (case-insensitive)

1 <i>or</i> <span class="smallblock">BLANK</span>&nbsp;or omitted: Shows 1 progress bar (simple form) = <span class="smallblock">DEFAULT</span>

2: Shows multiple progress bars for detailed examination of progress

# Examples

{% highlight php %}
Example #1
{% endhighlight %}

{% highlight php %}
<?php

define('_MPDF_URI','../');     // must be  a relative or absolute URI - not a file system path

$mpdf=new mPDF();

$mpdf->StartProgressBarOutput(2);

$mpdf->WriteHTML('You will hardly have time to see the progress bars!');

$mpdf->Output();

?>
{% endhighlight %}

# See Also

<ul>
<li class="manual_boxlist"><a href="{{ "/reference/mpdf-variables/progressbar.html" | prepend: site.baseurl }}">progressBar</a> –Specify whether to show progress bars during file generation</li>
<li class="manual_boxlist"><a href="{{ "/reference/mpdf-variables/progbar-heading.html" | prepend: site.baseurl }}">progbar_heading</a> - define customised heading for progress bars</li>
<li class="manual_boxlist"><a href="{{ "/reference/mpdf-variables/progbar-althtml.html" | prepend: site.baseurl }}">progbar_altHTML</a> - define customised HTML for progress bars

</li>
</ul>

