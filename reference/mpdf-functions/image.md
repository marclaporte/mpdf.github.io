---
layout: page
title: Image()
parent_title: mPDF functions
permalink: /reference/mpdf-functions/image.html
modification_time: 2015-08-05T12:00:47+00:00
---

See <a href="{{ "/what-else-can-i-do/images.html" | prepend: site.baseurl }}">Images</a>.

Image($filename, $x, $y, $width, $height, $ext, $href_link, $paint=true, $constrain=true, $is_watermark=false)

{% highlight php %}
<?php

$mpdf->Image('files/images/frontcover.jpg',0,0,210,297,'jpg','',true, false);

// the last "false" allows a full page picture
{% endhighlight %}

See Also

<ul>
<li class="manual_boxlist"><a href="{{ "/reference/mpdf-functions/setalpha.html" | prepend: site.baseurl }}">SetAlpha()</a> - Set the opacity and blend mode for Images</li>
</ul>

