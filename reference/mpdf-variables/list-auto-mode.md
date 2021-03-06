---
layout: page
title: list_auto_mode
parent_title: mPDF Variables
permalink: /reference/mpdf-variables/list-auto-mode.html
modification_time: 2015-08-05T12:02:07+00:00
---

(mPDF &gt;= 6.0)

# Description

void <b>list_auto_mode</b>

Specify whether to use mPDF custom method of automatic indentation of lists, or standard browser-compatible. The custom mPDF method is ignored if <code>list-style-position: inside</code>, or image used for marker (or custom U+).

For more information, see <a href="{{ "/what-else-can-i-do/lists.html" | prepend: site.baseurl }}">Lists</a>.

# Values

<span class="parameter">list_auto_mode</span>

<b>Values</b>

browser - list display will conform to standard browser behaviour for automatic indentation of lists

mpdf - list display will be consistent with mPDF behaviour prior to v6.0

<span class="smallblock">DEFAULT</span>: browser

# Changelog

<table class="table"> <thead>
<tr> <th>Version</th><th>Description</th> </tr>
</thead> <tbody>
<tr>
<td>6.0</td>
<td>Variable was added.</td>
</tr>
</tbody> </table>

# See Also

<ul>
<li class="manual_boxlist"><a href="{{ "/what-else-can-i-do/lists.html" | prepend: site.baseurl }}">Lists </a></li>
</ul>
