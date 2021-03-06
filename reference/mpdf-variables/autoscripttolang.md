---
layout: page
title: autoScriptToLang
parent_title: mPDF Variables
permalink: /reference/mpdf-variables/autoscripttolang.html
modification_time: 2015-08-05T12:01:41+00:00
---

<div>
<div>
<div>

(mPDF &gt;= 6.0)

# Description

boolean <b>autoScriptToLang</b>

When <span class="smallblock">TRUE</span>, <code>marks up HTML text using the lang attribute, based on the Unicode script block in question, and configurable values in <span class="code">config_script2lang.php</code>.</span>

# Values

<span class="parameter">autoScriptToLang</span> = <i><span class="smallblock">TRUE</span></i>|<span class="smallblock">FALSE</span>

<b>Values</b>

<i><span class="smallblock">TRUE</span></i>: <span class="smallblock">DEFAULT</span> mark up HTML text using the lang attribute, based on the Unicode script block in question, and configurable values in <code>config_script2lang.php</code>.

<span class="smallblock">FALSE</span>: No markup applied.

# See Also

<ul>
<li class="manual_boxlist"><a href="{{ "/reference/mpdf-variables/autolangtofont.html" | prepend: site.baseurl }}">autoLangToFont</a> - selects the font to use, based on the HTML lang attribute, using configurable values in <code>config_lang2font.php</code></li>
<li class="manual_boxlist"><a href="{{ "/fonts-languages/automatic-font-selection.html" | prepend: site.baseurl }}">Automatic Font selection</a> </li>
</ul>

</div>
</div>
</div>
