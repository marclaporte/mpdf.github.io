---
layout: page
title: Introduction
parent_title: CSS & Stylesheets
permalink: /css-stylesheets/introduction.html
modification_time: 2015-08-05T11:59:56+00:00
---

Default CSS styles are defined in <span class="filename">config.php</span> file (as <code>var $default_CSS</code>) which is based on the recommended default values for HTML4 - <a href="http://www.w3.org/TR/CSS21/sample.html">http://www.w3.org/TR/CSS21/sample.html</a> The appearance of a default mPDF document based on HTML should approximate to its appearance in a browser.

The following are supported (in order of ascending priority - lower ones in list overwrite higher):

<ul>
<li>HTML attributes e.g. &lt;div align="center"&gt; (see <a href="{{ "/html-support/html-attributes.html" | prepend: site.baseurl }}">supported HTML attributes</a>)</li>
<li>CSS Stylesheets - included in header of HTML document or as &lt;link&nbsp; /&gt; or as @import()
<ul>
<li>- html tags e.g. p { font-size:12pt; color:#880000; }</li>
<li>- class e.g. .stylename { font-size:9pt; }</li>
<li>- id e.g. #style { font-size:9pt; }</li>
</ul>
</li>
<li>In-line CSS style e.g. &lt;p style="font-family:monospace;"&gt;</li>
</ul>

Note: Prior to mPDF 5.x HTML attributes overrode CSS styles.

CSS attributes, used in stylesheets or in-line, can define:

<ul>
<li>most tags/elements e.g. div, p, body, table, span</li>
<li>class-names e.g. p.mystylename { font-size:9pt; }</li>
<li>id e.g. div#style { font-size:9pt; }</li>
</ul>

Tag, class and id can share a similar name e.g. p {...} .p {...} and #p {...} are handled uniquely

There is some support for 'cascaded' CSS e.g. div.topic table.type1 td {...}

- table, tr, th and td will only be recognised as the last items (as above)

- only 'block' elements (not 'in-line') can be included i.e. div.style1 a {...} will not work, nor will a#class1 {...}

For a full list of CSS attributes supported see <a href="{{ "/css-stylesheets/supported-css.html" | prepend: site.baseurl }}">Supported CSS</a>

Note the OUTLINE style (which is not supported in most browsers) does work in mPDF e.g.

&lt;span style="outline-width:thin|medium|thick; outline-color:#rrggbb|invert"&gt;

# Using a stylesheet

The WriteHTML() method takes second parameter i.e. <span class="parameter">mode</span>. See <a href="{{ "/reference/mpdf-functions/writehtml.html" | prepend: site.baseurl }}">WriteHTML()</a> for details of this and other parameters.

<span class="parameter">mode</span>

0 - Use this (default) if the text you pass is a complete HTML page including head and body and style definitions.

1 - Use this when you want to set a CSS stylesheet - see example below

2 - Write HTML code without the &lt;head&gt; information. Does not need to be contained in &lt;body&gt;

{% highlight php %}
Example using a stylesheet
{% endhighlight %}

{% highlight php %}
<?php

$stylesheet = file_get_contents('style.css');

$mpdf->WriteHTML($stylesheet,1);

$mpdf->WriteHTML($html,2);
{% endhighlight %}

# Media selectors

mPDF supports media-dependent CSS styles as:

{% highlight php %}
@media print { 

 p { color: red; } 

}

<style media="print">

 p { color: red; } 

</style>

<link rel="stylesheet" media="print" href="..." />
{% endhighlight %}

By default mPDF will match stylesheets set for "print" or "all" media. This can be changed by the configurable variable <a href="{{ "/reference/mpdf-variables/cssselectmedia.html" | prepend: site.baseurl }}">CSSselectMedia</a>.

