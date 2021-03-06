---
layout: page
title: Supported CSS
parent_title: CSS & Stylesheets
permalink: /css-stylesheets/supported-css.html
modification_time: 2015-08-05T11:59:56+00:00
---

# Supported CSS attributes - stylesheets or in-line

Unless otherwise stated, the following values are supported:

<span class="smallblock">LENGTH</span>: px, pc, pt, cm, mm, in, em, rem, ex and % (where appropriate) are supported. Default if no unit given is px.

<span class="smallblock">FONT-SIZE</span>: px, pc, pt, em, rem, ex, %, small, medium, large, x-small, x-large&nbsp; are supported. Default if no unit given is px.

<div class="alert alert-info" role="alert"><strong>Note:</strong> Support for "rem" was added mPDF 5.7&nbsp; Unlike the CSS3 specification, the basic size used for rem in the document is based on the font-size set on the &lt;body&gt; element (rather than the &lt;html&gt; element).</div>

Conversion from "px" is determined by the configurable variables <a href="{{ "/reference/mpdf-variables/dpi.html" | prepend: site.baseurl }}">dpi</a> and <a href="{{ "/reference/mpdf-variables/img-dpi.html" | prepend: site.baseurl }}">img_dpi</a>

"ex" uses an approximation of half the font height

<span class="smallblock">FONT-FAMILY</span>: Any font family defined in your configuration, as well as <i>sans</i>, <i>sans-serif</i>, <i>serif</i> or <i>monospace</i>.

<span class="smallblock">COLOR</span>: #rgb or #rrggbb or rgb(255,255,255) or <a href="{{ "/css-stylesheets/named-colours.html" | prepend: site.baseurl }}">colour names</a> e.g. 'black', 'gray' are supported.

Also supported are:

<ul>
<li>rgb(255,255,255)</li>
<li>rgba(255,255,255,1) <i>[last value is transparency (alpha) - between 0-1]*</i></li>
<li>rgb(100%,100%,100%)</li>
<li>hsl(360,100%,100%)</li>
<li>hsla(360,100%,100%,1) <i>[last value is transparency (alpha) - between 0-1]*</i></li>
<li>cmyk(100,100,100,100) <i>[or 0-100%]</i></li>
<li>cmyka(100,100,100,100,1) <i>[or 0-100%; last value is transparency (alpha) - between 0-1]*</i></li>
<li>device-cmyk(100,100,100,100) <i>[or 0-100%]</i></li>
<li><i>device-cmyka</i>(100,100,100,100,1) <i>[or 0-100%; last value is transparency (alpha) - between 0-1]*</i></li>
<li>spot(COLOR NAME, 100%). (cf. <a href="{{ "/reference/mpdf-functions/addspotcolor.html" | prepend: site.baseurl }}">AddSpotColor</a>)</li>
</ul>

mPDF&nbsp; &gt;= 5.7 Spotcolor CMYK values can be defined as it is used e.g. color: spot(PANTONE 534 EC, 100%, 85, 65, 47, 9);

*Alpha values (transparency) are only supported on background colours - not text color

<table class="table"> <thead>
<tr> <th>HTML&nbsp;Tag</th>
<td>Property</td>
<td>Values allowed &amp; Notes

</td>
</tr>
</thead> <tbody>
<tr> <th rowspan="9">BODY</th>
<td>direction

</td>
<td>rtl | ltr (mPDF &gt;= 5.0)</td>
</tr>
<tr>
<td><span class="smallblock">COMMON TEXT STYLES</span>

</td>
<td><span class="smallblock">See below - all excpet text-shadow

</span></td>
</tr>
<tr>
<td><i>margin-collapse</i></td>
<td>collapse | none (custom attribute - collapses top and bottom margins if at top or bottom of page)</td>
</tr>
<tr>
<td>line-height</td>
<td>Line height as a factor of font-height. Usual values around 1.2 or 1.3

Also accepts px, pc, pt, cm, mm, in, em and % (mPDF &gt;= 4.0)</td>
</tr>
<tr>
<td>background, background-image, background-position, background-repeat, background-color</td>
<td>

background is parsed as per the CSS specification.

background-image in the form url(image.png) or url('image.png') or <span class="smallblock">GRADIENT</span> (mPDF &gt;= 5.1).

background-position is supported as per CSS2.1

background-repeat: repeat | repeat-x | repeat-y | no-repeat

background-attachment is parsed but has no effect.

See note below. (cf. <a href="{{ "/what-else-can-i-do/backgrounds-borders.html" | prepend: site.baseurl }}">Backgrounds &amp; borders</a>)

(All except background-color added mPDF 3.0)

</td>
</tr>
<tr>
<td><i>background-image-resolution</i></td>
<td>

normal | [ from-image 

 &lt;dpi&gt; ]&nbsp; (mPDF &gt;= 5.1)

Custom tag, but as for image-resolution in CSS3

</td>
</tr>
<tr>
<td><i>background-gradient</i></td>
<td>

Defines a linear or radial colour gradient for the background.

linear <span class="smallblock">COLOR1 </span><span class="smallblock">COLOR2</span> x1 y1 x2 y2; or

radial <span class="smallblock">COLOR1 </span><span class="smallblock">COLOR2</span> x1 y1 x2 y2 radius;

x, y and radius are values between 0 and 1

(custom attribute) (cf. <a href="{{ "/what-else-can-i-do/backgrounds-borders.html" | prepend: site.baseurl }}">Backgrounds &amp; borders</a>)

</td>
</tr>
<tr>
<td><i>background-image-opacity</i></td>
<td>

Value between 0 and 1.0

Sets the opacity/transparency of the background image.

</td>
</tr>
<tr>
<td><i>background-image-resize</i></td>
<td>0 - No resizing (default)

1 - Shrink-to-fit w (keep aspect ratio)

2 - Shrink-to-fit h (keep aspect ratio)

3 - Shrink-to-fit w and/or h (keep aspect ratio)

4 - Resize-to-fit w (keep aspect ratio)

5 - Resize-to-fit h (keep aspect ratio)

6 - Resize-to-fit w and h</td>
</tr>
<tr> <th rowspan="30">

All Block level tags:

P, DIV, H1-H6, OL, UL, ADDRESS,

BLOCKQUOTE, CAPTION,

CENTER, DL, DT, DD, FORM,

ARTICLE, ASIDE, DETAILS,

FIELDSET, FIGURE,

FIGCAPTION, FOOTER,

HEADER, HGROUP, NAV,

SECTION, SUMMARY

</th>
<td>margin*, margin-top, margin-bottom, margin-left, margin-right</td>
<td>

<span class="smallblock">LENGTH</span>

</td>
</tr>
<tr>
<td>padding*, padding-right, padding-left, padding-top, padding-bottom</td>
<td>

<span class="smallblock">LENGTH</span>

</td>
</tr>
<tr>
<td>border, border-top, border-bottom, border-left, border-right</td>
<td>

Size style and colour e.g.

<span class="smallblock">LENGTH</span> solid|dotted|dashed|double <span class="smallblock">COLOR</span>

</td>
</tr>
<tr>
<td>border-color*, border-top-color, border-right-color, border-bottom-color, border-left-color</td>
<td>

<span class="smallblock">COLOR</span>

(mPDF &gt;= 4.0)

</td>
</tr>
<tr>
<td>border-width*, border-top-width, border-right-width, border-bottom-width, border-left-width</td>
<td>

<span class="smallblock">LENGTH</span>&nbsp;

(mPDF &gt;= 4.0)</td>
</tr>
<tr>
<td>border-style*, border-top-style, border-right-style, border-bottom-style, border-left-style</td>
<td>

solid|dotted|dashed|double

(mPDF &gt;= 4.0)

(double was added mPDF 4.2)

</td>
</tr>
<tr>
<td>border-radius, border-top-left-radius, border-top-right-radius, border-bottom-right-radius, border-bottom-left-radius</td>
<td><span class="smallblock">LENGTH</span>

See <a href="http://www.w3.org/TR/2008/WD-css3-background-20080910/#layering">draft CSS3 specification</a> for use.

NB Use of $autoPadding which can automatically increase padding in block elements with border-radius set as required</td>
</tr>
<tr>
<td>width</td>
<td>

<span class="smallblock">LENGTH</span>

mPDF does not support nested block elements which overlap (horizontally or vertically) i.e. the inner block must be contained by the outer block's physical dimensions. width and height are overridden if this is not the case.

</td>
</tr>
<tr>
<td>height</td>
<td>

<span class="smallblock">LENGTH</span>&nbsp;

mPDF does not support nested block elements which overlap (horizontally or vertically) i.e. the inner block must be contained by the outer block's physical dimensions. width and height are overridden if this is not the case.

(Prior to mPDF v5.1: only supported if whole block is all on one page; will extend a block but not shorten it; will not force a pagebreak even if height should move onto next page.)

NB % is interpreted as % of printable page height (inside margins)

</td>
</tr>
<tr>
<td>text-align</td>
<td>left | center | right | justify</td>
</tr>
<tr>
<td>page-break-after</td>
<td>auto | avoid | always | left | right (extended mPDF &gt;= 5.4)

</td>
</tr>
<tr>
<td>page-break-inside</td>
<td>avoid (avoids a page-break within the block - only works across max. of 2 pages; not compatible with table autosize or table rotate)</td>
</tr>
<tr>
<td>page-break-before</td>
<td>always | left | right</td>
</tr>
<tr>
<td>display</td>
<td>none</td>
</tr>
<tr>
<td>visibility</td>
<td>visible | hidden | <i>printonly</i> | <i>screenonly</i>&nbsp; (mPDF &gt;= 5.4)

</td>
</tr>
<tr>
<td><i>margin-collapse</i></td>
<td>collapse|none (custom attribute - collapses top and bottom margins if at top or bottom of page)</td>
</tr>
<tr>
<td>line-height</td>
<td>

Line height as a factor of font-height. Usual values around 1.2 or 1.3

Also accepts px, pc, pt, cm, mm, in, em and % (mPDF &gt;= 4.0)

'normal' also accepted (set by default to 1.3 in mPDF)

</td>
</tr>
<tr>
<td>line-stacking-strategy</td>
<td>

inline-line-height | block-line-height | max-height | grid-height

As per draft CSS3 spec. (mPDF &gt;= 6.0)

Default = inline-line-height

</td>
</tr>
<tr>
<td>line-stacking-shift</td>
<td>

consider-shifts | disregard-shifts

As per draft CSS3 spec. (mPDF &gt;= 6.0)

Default = consider-shifts

</td>
</tr>
<tr>
<td>background, background-image, background-position, background-repeat, background-color</td>
<td>

background is parsed as per the CSS specification.

background-image in the form url(image.png) or url('image.png') or <span class="smallblock">GRADIENT</span> (mPDF &gt;= 5.1).

background-position is supported as per CSS2.1

background-repeat: repeat | repeat-x | repeat-y | no-repeat

background-attachment is parsed but has no effect.

See note below. (cf. <a href="{{ "/what-else-can-i-do/backgrounds-borders.html" | prepend: site.baseurl }}">Backgrounds &amp; borders</a>)

(All except background-color added mPDF 3.0)

</td>
</tr>
<tr>
<td>background-clip</td>
<td>

padding-box|border-box (default=border-box)

extended to include "content-box" from mPDF 5.7

</td>
</tr>
<tr>
<td>background-origin</td>
<td>

padding-box|content-box|border-box&nbsp; (default padding-box)

As per CSS3. mPDF &gt;= 5.7

</td>
</tr>
<tr>
<td>background-size</td>
<td>

[ &lt;length&gt; | &lt;percentage&gt; | auto ]{1,2} | cover | contain&nbsp; (default = auto)

As per CSS3. mPDF &gt;= 5.7

</td>
</tr>
<tr>
<td><i>background-image-resolution</i></td>
<td>

normal | [ from-image 

 &lt;dpi&gt; ]&nbsp; (mPDF &gt;= 5.1)

Custom tag, but as for image-resolution in CSS3

</td>
</tr>
<tr>
<td><i>background-gradient</i></td>
<td>

Defines a linear or radial colour gradient for the background.

linear <span class="smallblock">COLOR1 </span><span class="smallblock">COLOR2</span> x1 y1 x2 y2; or

radial <span class="smallblock">COLOR1 </span><span class="smallblock">COLOR2</span> x1 y1 x2 y2 radius;

x, y and radius are values between 0 and 1

(custom attribute) (cf. <a href="{{ "/what-else-can-i-do/backgrounds-borders.html" | prepend: site.baseurl }}">Backgrounds &amp; borders</a>)

</td>
</tr>
<tr>
<td><i>background-image-opacity</i></td>
<td>

Value between 0 and 1.0

Sets the opacity/transparency of the background image.

</td>
</tr>
<tr>
<td><i>background-image-resize</i></td>
<td>0 - No resizing (default)

1 - Shrink-to-fit w (keep aspect ratio)

2 - Shrink-to-fit h (keep aspect ratio)

3 - Shrink-to-fit w and/or h (keep aspect ratio)

4 - Resize-to-fit w (keep aspect ratio)

5 - Resize-to-fit h (keep aspect ratio)

6 - Resize-to-fit w and h</td>
</tr>
<tr>
<td>

box-shadow

</td>
<td>

As per CSS3 specification. 'inset' is not supported.

(mPDF &gt;= 5.4)

</td>
</tr>
<tr>
<td>box-decoration-break</td>
<td>

slice | clone&nbsp; (default = slice)

Defines the handling of padding and borders at page breaks, when <a href="{{ "/paging/page-breaks.html" | prepend: site.baseurl }}">clonebycss</a> set

</td>
</tr>
<tr>
<td>z-index</td>
<td>

Sets a layer in the PDF document.

Note: this is not the same as a "layer" in CSS terms. See <a href="{{ "/what-else-can-i-do/layers.html" | prepend: site.baseurl }}">Layers</a>.

</td>
</tr>
<tr> <th rowspan="11">

All Block level tags:

P, DIV, H1-H6, OL, UL, ADDRESS,

BLOCKQUOTE, CAPTION,

CENTER, DL, DT, DD, FORM,

ARTICLE, ASIDE, DETAILS,

FIELDSET, FIGURE, FIGCAPTION, FOOTER,

HEADER, HGROUP, NAV,

SECTION, SUMMARY

(contd.)

</th>
<td><span class="smallblock">COMMON TEXT STYLES</span></td>
<td><span class="smallblock">See below</span></td>
</tr>
<tr>
<td>

<i>text-indent</i>

</td>
<td>

Indents first line of text in the paragraph/block.

<span class="smallblock">LENGTH</span>

(Indent is disabled in tables.)

Negative value will give a 'hanging indent'.

</td>
</tr>
<tr>
<td>position</td>
<td>fixed | absolute

absolute - uses physical page as containing element;

fixed - uses printable page (inside margins) as containing element.

(mPDF &gt;= 4.0)

NB Only supported for top-level elements i.e. where the parent element is &lt;body&gt;. Fixed-position or floating elements nested inside other fixed-position or floating elements are not supported.

</td>
</tr>
<tr>
<td>overflow</td>
<td>

visible | hidden | auto

Applies to block elements with position fixed or absolute. auto - causes text to autofit within the block size (constrained if necessary to page edges).

(mPDF &gt;= 4.0)

</td>
</tr>
<tr>
<td>hyphens</td>
<td>

none | manual | auto (default = manual)

As per CSS. (mPDF&nbsp; &gt;= 5.7)

</td>
</tr>
<tr>
<td><i>rotate</i></td>
<td>

90 | -90

Applies only to block elements with position fixed or absolute. (mPDF &gt;= 5.0)

Sizing and layout of the block element using top, left, bottom, right, width and height are applied BEFORE the element is rotated. The top and left co-ordinates are respected for positioning, except when bottom or right are specified without respective top or left when the bottom/right co-ordinates are used.

</td>
</tr>
<tr>
<td>top, left, bottom, right</td>
<td>

<span class="smallblock">LENGTH</span>

Applies to block elements with position fixed or absolute.

(mPDF &gt;= 4.0)

</td>
</tr>
<tr>
<td>float</td>
<td>

left|right

Partially supported as for CSS2 property.

NB Fixed-position or floating elements nested inside other fixed-position or floating elements are not supported.

</td>
</tr>
<tr>
<td>clear</td>
<td>left|right|both</td>
</tr>
<tr>
<td>page</td>
<td>Specify a named page selector (see @page)</td>
</tr>
<tr>
<td>direction</td>
<td>rtl | ltr (mPDF &gt;= 5.1)</td>
</tr>
</tbody> </table>
<table class="table"> <thead>
<tr> <th>HTML Tag</th>
<td>Property</td>
<td>Values allowed &amp; Notes

</td>
</tr>
</thead> <tbody>
<tr> <th rowspan="5">

LIST tags: OL, UL

</th>
<td>list-style</td>
<td>[ 'list-style-type' 

 'list-style-position' 

 'list-style-image' ]&nbsp;&nbsp; mPDF &gt;= 6.0</td>
</tr>
<tr>
<td>list-style-type<i>&nbsp;</i></td>
<td>
<ul> </li>
</ul>

1 | A | a | I | i | disc | circle | square | decimal | lower-roman | upper-roman | lower-latin | upper-latin | lower-alpha | upper-alpha | none

arabic-indic | bengali | cambodian | cjk-decimal | devanagari | gujarati | gurmukhi | hebrew |kannada | khmer | lao | malayalam | oriya | persian | telugu | thai | urdu | tamil

"1" - decimal

"A" = upper-latin

"a" = lower-latin

"I" = upper-roman

"i" = lower-roman

Custom list-style-type is recognised e.g.: U+263Argb(255,0,0);

- where U+263A is the Unicode HEX value of the character you want for the bullet 

- the character MUST be included in the font used for that list item

- rgb() bit is optional

</td>
</tr>
<tr>
<td>list-style-image</td>
<td>

<span class="smallblock">&lt;URI&gt;</span>

mPDF &gt;= 6.0

</td>
</tr>
<tr>
<td>list-style-position</td>
<td>

inside | outside&nbsp; (default = outside)

mPDF &gt;= 6.0

</td>
</tr>
<tr>
<td>&nbsp;</td>
<td><b>NB Lists are handled as block-level elements as from mPDF 6.0 (see above)</b></td>
</tr>
<tr> <th rowspan="5">

LI

</th>
<td>list-style</td>
<td>

[ 'list-style-type' 

 'list-style-position' 

 'list-style-image' ]&nbsp;&nbsp; mPDF &gt;= 6.0

</td>
</tr>
<tr>
<td>list-style-type<i>&nbsp;</i></td>
<td>

1 | A | a | I | i | disc | circle | square | decimal | lower-roman | upper-roman | lower-latin | upper-latin | lower-alpha | upper-alpha | none

arabic-indic | bengali | cambodian | cjk-decimal | devanagari | gujarati | gurmukhi | hebrew |kannada | khmer | lao | malayalam | oriya | persian | telugu | thai | urdu | tamil

"1" - decimal

"A" = upper-latin

"a" = lower-latin

"I" = upper-roman

"i" = lower-roman

Custom list-style-type is recognised e.g.: U+263Argb(255,0,0);

- where U+263A is the Unicode HEX value of the character you want for the bullet 

- the character MUST be included in the font used for that list item

- rgb() bit is optional

</td>
</tr>
<tr>
<td>list-style-image</td>
<td>

<span class="smallblock">&lt;URI&gt;</span>

mPDF &gt;= 6.0</td>
</tr>
<tr>
<td>list-style-position</td>
<td>

inside | outside&nbsp; (default = outside)

mPDF &gt;= 6.0

</td>
</tr>
<tr>
<td>&nbsp;</td>
<td><b>NB Lists are handled as block-level elements as from mPDF 6.0 (see above)</b></td>
</tr>
</tbody> </table>
<table class="table"> <thead>
<tr> <th>

HTML Tag

</th>
<td>Property</td>
<td>Values allowed &amp; Notes

</td>
</tr>
</thead> <tbody>
<tr> <th rowspan="9">

All Inline tags:

SPAN, A, SUB, SUP,&nbsp; ACRONYM,

BIG, SMALL, INS, S, STRIKE,

DEL, STRONG, CITE, Q, EM,

B, I, U, SAMP, CODE, KBD, TT,

VAR, FONT, TIME, MARK

</th>
<td><span class="smallblock">COMMON TEXT STYLES</span></td>
<td><span class="smallblock">See below</span></td>
</tr>
<tr>
<td>border, border-top, border-bottom, border-left, border-right</td>
<td>

Size style and colour e.g.

<span class="smallblock">LENGTH</span> solid|dotted|dashed|double <span class="smallblock">COLOR</span>

(mPDF &gt;= 5.4)

</td>
</tr>
<tr>
<td>

border-color*, border-top-color, border-right-color, border-bottom-color, border-left-color

</td>
<td>

<span class="smallblock">COLOR</span>

(mPDF &gt;= 5.4)

</td>
</tr>
<tr>
<td>

border-width*, border-top-width, border-right-width, border-bottom-width, border-left-width

</td>
<td>

<span class="smallblock">LENGTH</span>&nbsp;

(mPDF &gt;= 5.4)</td>
</tr>
<tr>
<td>

border-style*, border-top-style, border-right-style, border-bottom-style, border-left-style

</td>
<td>

solid|dotted|dashed|double

(mPDF &gt;= 5.4)

</td>
</tr>
<tr>
<td>background-color, background</td>
<td><span class="smallblock">COLOR</span> (only the color is supported in background)

</td>
</tr>
<tr>
<td>display</td>
<td>none (mPDF &gt;= 5.0)</td>
</tr>
<tr>
<td>visibility</td>
<td>

hidden | visible | printonly | screenonly (default = visible)

(mPDF &gt;= 5.7)

</td>
</tr>
<tr>
<td>hyphens</td>
<td>

none | manual | auto (default = manual)

As per CSS. (mPDF&nbsp; &gt;= 5.7)</td>
</tr>
</tbody> </table>
<table class="table"> <thead>
<tr> <th style="white-space: nowrap;">HTML Tag</th>
<td>Property</td>
<td>Values allowed &amp; Notes

</td>
</tr>
</thead> <tbody>
<tr> <th rowspan="28">TABLE</th>
<td>background-color</td>
<td><span class="smallblock">COLOR</span></td>
</tr>
<tr>
<td>background, background-image, background-position, background-repeat, background-color</td>
<td>

background is parsed as per the CSS specification.

background-image in the form url(image.png) or url('image.png') or <span class="smallblock">GRADIENT</span>.

background-position is supported as per CSS2.1

background-repeat: repeat | repeat-x | repeat-y | no-repeat

background-attachment is parsed but has no effect.

See note below. (cf. <a href="{{ "/what-else-can-i-do/backgrounds-borders.html" | prepend: site.baseurl }}">Backgrounds &amp; borders</a>)

(All except background-color added mPDF 5.1)

</td>
</tr>
<tr>
<td>background-image-resolution</td>
<td>normal | [ from-image 

 &lt;dpi&gt; ]&nbsp; (mPDF &gt;= 5.1)</td>
</tr>
<tr>
<td><i>background-image-opacity</i></td>
<td>

Value between 0 and 1.0

Sets the opacity/transparency of the background image.

</td>
</tr>
<tr>
<td><span class="smallblock">COMMON TEXT STYLES</span></td>
<td><span class="smallblock">See below - except text-decoration, text-trnsform and text-shadow

</span></td>
</tr>
<tr>
<td>

border, border-right, border-left, border-top, border-bottom

</td>
<td>

Size style and colour e.g.

<span class="smallblock">LENGTH</span> double | solid | dashed | dotted | ridge | outset | groove | inset | hidden | none <span class="smallblock">COLOR</span>&nbsp;

NB Table &amp; cell borders accept: double | solid | dashed | dotted | ridge | outset | groove | inset (other block elements only support solid | dotted | dashed | double)

</td>
</tr>
<tr>
<td>border-color*, border-top-color, border-right-color, border-bottom-color, border-left-color</td>
<td>

<span class="smallblock">COLOR</span>

(mPDF &gt;= 4.0)

</td>
</tr>
<tr>
<td>border-width*, border-top-width, border-right-width, border-bottom-width, border-left-width</td>
<td>

<span class="smallblock">LENGTH</span>&nbsp;

(mPDF &gt;= 4.0)</td>
</tr>
<tr>
<td>border-style*, border-top-style, border-right-style, border-bottom-style, border-left-style</td>
<td>

double | solid | dashed | dotted | ridge | outset | groove | inset | hidden | none

(mPDF &gt;= 4.0)

</td>
</tr>
<tr>
<td>padding*, padding-right, padding-left, padding-top, padding-bottom</td>
<td>

<span class="smallblock">LENGTH</span>

(mPDF &lt;= 1.3 incorrectly set cell-padding for all cells in table.)

Sets table padding (only relevant when border-collapse:separate)

</td>
</tr>
<tr>
<td>margin*, margin-right, margin-left, margin-top, margin-bottom</td>
<td><span class="smallblock">LENGTH</span></td>
</tr>
<tr>
<td>width</td>
<td><span class="smallblock">LENGTH</span></td>
</tr>
<tr>
<td>vertical-align</td>
<td>top | middle | bottom (applies to all cells in table)</td>
</tr>
<tr>
<td>text-align</td>
<td>left | right | center (applies to all cells in table; to centre a table on the page, you must use the align="center" attribute in the table tag)</td>
</tr>
<tr>
<td>border-collapse</td>
<td>collapse | separate</td>
</tr>
<tr>
<td>border-spacing</td>
<td>

Single or double values:

2px sets horizontal and vertical;

2px 3px sets horizontal=2 and vertical=3

(Same as cellSpacing attribute) Default=2px

</td>
</tr>
<tr>
<td>empty-cells</td>
<td>hide | show (only relevant when border-collapse:separate)</td>
</tr>
<tr>
<td>page-break-inside</td>
<td>avoid</td>
</tr>
<tr>
<td>page-break-after</td>
<td>left | right | always

(mPDF &gt;= 5.4)</td>
</tr>
<tr>
<td><i>rotate</i></td>
<td>rotates the table 90 degress clockwise (90) or counter-clockwise (-90). Does not work with columns, and bookmarks will not be correctly placed (custom attribute)</td>
</tr>
<tr>
<td><i>autosize</i></td>
<td>Shrinks a table to fit if width is too small to allow complete words to fit. The value (must be &gt;=1) determines the maximum allowable factor to shrink i.e. autosize="2" will allow the font-size to be reduced to a minimum of 1/2 the original size. A value of 1 prevents automatic resizing of the table. (custom property)</td>
</tr>
<tr>
<td><i>topntail</i></td>
<td>Sets border at top and bottom of table, and below THEAD row if present. (custom attribute)</td>
</tr>
<tr>
<td><i>thead-underline</i></td>
<td>Sets border at bottom of THEAD row if present. (custom attribute added mPDF v1.1)</td>
</tr>
<tr>
<td>line-height</td>
<td>Sets default line-height for table cells as factor or % (value e.g. 1.3)</td>
</tr>
<tr>
<td>line-stacking-strategy</td>
<td>inline-line-height | block-line-height | max-height | grid-height

As per draft CSS3 spec. (mPDF &gt;= 6.0)

Default = inline-line-height</td>
</tr>
<tr>
<td>line-stacking-shift</td>
<td>consider-shifts | disregard-shifts

As per draft CSS3 spec. (mPDF &gt;= 6.0)

Default = consider-shifts</td>
</tr>
<tr>
<td><i>overflow</i></td>
<td>auto | hidden | visible | wrap

Controls table layout if minimum width is too wide for page.</td>
</tr>
<tr>
<td>direction</td>
<td>rtl | ltr (mPDF &gt;= 5.1)</td>
</tr>
<tr> <th>

CAPTION

</th>
<td>caption-side</td>
<td>top | bottom (mPDF &gt;= 5.4) Right and left are not supported

</td>
</tr>
<tr>
<td rowspan="3"><b>THEAD, TFOOT</b></td>
<td>font-weight</td>
<td>normal | bold</td>
</tr>
<tr>
<td>vertical-align</td>
<td>top | middle | bottom</td>
</tr>
<tr>
<td>text-align</td>
<td>left | center | right</td>
</tr>
<tr> <th rowspan="9">TR</th>
<td>background-color</td>
<td><span class="smallblock">COLOR</span></td>
</tr>
<tr>
<td>background, background-image, background-position, background-repeat, background-color</td>
<td>

background is parsed as per the CSS specification.

background-image in the form url(image.png) or url('image.png') or <span class="smallblock">GRADIENT</span>.

background-position is supported as per CSS2.1

background-repeat: repeat | repeat-x | repeat-y | no-repeat

background-attachment is parsed but has no effect.

See note below. (cf. <a href="{{ "/what-else-can-i-do/backgrounds-borders.html" | prepend: site.baseurl }}">Backgrounds &amp; borders</a>)

(All except background-color added mPDF 5.1)

</td>
</tr>
<tr>
<td><i>background-image-opacity</i></td>
<td>

Value between 0 and 1.0

Sets the opacity/transparency of the background image.

</td>
</tr>
<tr>
<td>border, border-right, border-left, border-top, border-bottom</td>
<td>

Size style and colour e.g.

<span class="smallblock">LENGTH</span> double | solid | dashed | dotted | ridge | outset | groove | inset | hidden | none <span class="smallblock">COLOR</span>&nbsp;

NB Table &amp; cell borders accept: double | solid | dashed | dotted | ridge | outset | groove | inset | hidden | none (other block elements only support solid | dotted | dashed | double)

(mPDF &gt;= 5.1)</td>
</tr>
<tr>
<td>border-color*, border-top-color, border-right-color, border-bottom-color, border-left-color</td>
<td>

<span class="smallblock">COLOR</span>

(mPDF &gt;= 5.1)

</td>
</tr>
<tr>
<td>border-width*, border-top-width, border-right-width, border-bottom-width, border-left-width</td>
<td>

<span class="smallblock">LENGTH</span>&nbsp;

(mPDF &gt;= 5.1)</td>
</tr>
<tr>
<td>border-style*, border-top-style, border-right-style, border-bottom-style, border-left-style</td>
<td>

double | solid | dashed | dotted | ridge | outset | groove | inset | hidden | none

(mPDF &gt;= 5.1)

</td>
</tr>
<tr>
<td><i>text-rotate</i></td>
<td>Rotate the text inside table cells for this row. Accepted values are 1 - 90 for degrees anticlockwise, or -90 (only) for clockwise rotation. (custom attribute)</td>
</tr>
<tr>
<td>:nth-child()&nbsp; <span class="smallblock">SELECTOR</span><i>&nbsp;</i></td>
<td>odd | even | <i>a</i>n+<i>b</i>

As per CSS3 specification</td>
</tr>
<tr> <th rowspan="21">TD, TH</th>
<td>background, background-image, background-position, background-repeat, background-color</td>
<td>

background is parsed as per the CSS specification.

background-image in the form url(image.png) or url('image.png') or <span class="smallblock">GRADIENT</span> (mPDF &gt;= 5.1).

background-position is supported as per CSS2.1

background-repeat: repeat | repeat-x | repeat-y | no-repeat

background-attachment is parsed but has no effect.

See note below.

(All except background-color added mPDF 3.2)

</td>
</tr>
<tr>
<td><i>background-gradient</i></td>
<td>

Defines a linear or radial colour gradient for the background.

linear <span class="smallblock">COLOR1 </span><span class="smallblock">COLOR2</span> x1 y1 x2 y2; or

radial <span class="smallblock">COLOR1 </span><span class="smallblock">COLOR2</span> x1 y1 x2 y2 radius;

x, y and radius are values between 0 and 1

(custom attribute) (cf. <a href="{{ "/what-else-can-i-do/backgrounds-borders.html" | prepend: site.baseurl }}">Backgrounds &amp; borders</a>)

(Added mPDF 3.2)

</td>
</tr>
<tr>
<td><i>background-image-opacity</i></td>
<td>

Value between 0 and 1.0

Sets the opacity/transparency of the background image.

</td>
</tr>
<tr>
<td><i>background-image-resize</i></td>
<td>0 - No resizing (default)

1 - Shrink-to-fit w (keep aspect ratio)

2 - Shrink-to-fit h (keep aspect ratio)

3 - Shrink-to-fit w and/or h (keep aspect ratio)

4 - Resize-to-fit w (keep aspect ratio)

5 - Resize-to-fit h (keep aspect ratio)

6 - Resize-to-fit w and h</td>
</tr>
<tr>
<td>

border, border-right, border-left, border-top, border-bottom

</td>
<td>

Size style and colour e.g.

<span class="smallblock">LENGTH</span> double | solid | dashed | dotted | ridge | outset | groove | inset | hidden | none <span class="smallblock">COLOR</span>&nbsp;

NB Table &amp; cell borders accept: double | solid | dashed | dotted | ridge | outset | groove | inset | hidden | none (other block elements only support solid | dotted | dashed | double)

</td>
</tr>
<tr>
<td>border-color*, border-top-color, border-right-color, border-bottom-color, border-left-color</td>
<td>

<span class="smallblock">COLOR</span>

(mPDF &gt;= 4.0)

</td>
</tr>
<tr>
<td>border-width*, border-top-width, border-right-width, border-bottom-width, border-left-width</td>
<td>

<span class="smallblock">LENGTH</span>&nbsp;

(mPDF &gt;= 4.0)</td>
</tr>
<tr>
<td>border-style*, border-top-style, border-right-style, border-bottom-style, border-left-style</td>
<td>

double | solid | dashed | dotted | ridge | outset | groove | inset | hidden | none

(mPDF &gt;= 4.0)

</td>
</tr>
<tr>
<td>padding*, padding-right, padding-left, padding-top, padding-bottom</td>
<td>

<span class="smallblock">LENGTH</span>

</td>
</tr>
<tr>
<td>width</td>
<td><span class="smallblock">LENGTH</span></td>
</tr>
<tr>
<td>height</td>
<td><span class="smallblock">LENGTH</span> (but not %) (mPDF &gt;= 4.0)

</td>
</tr>
<tr>
<td><span class="smallblock">COMMON TEXT STYLES</span></td>
<td><span class="smallblock">See below</span></td>
</tr>
<tr>
<td>white-space</td>
<td>nowrap</td>
</tr>
<tr>
<td>vertical-align</td>
<td>top|middle|bottom</td>
</tr>
<tr>
<td>text-align</td>
<td>

left | right | center

From mPDF 5.7, also supports a decimal-mark alignment followed by a default e.g.

text-align: '.' center;

Non-ASCII characters should be defined using Unicode values:

text-align: '\66B' center;

</td>
</tr>
<tr>
<td><i>text-rotate</i></td>
<td>Rotates the text in a table cell. Accepted values are 1-90 for degrees anticlockwise, or -90 (only) for clockwise rotation. (custom attribute)</td>
</tr>
<tr>
<td>line-stacking-strategy</td>
<td>inline-line-height | block-line-height | max-height | grid-height

As per draft CSS3 spec. (mPDF &gt;= 6.0)

Default = inline-line-height</td>
</tr>
<tr>
<td>line-stacking-shift</td>
<td>consider-shifts | disregard-shifts

As per draft CSS3 spec. (mPDF &gt;= 6.0)

Default = consider-shifts</td>
</tr>
<tr>
<td>hyphens<i>&nbsp;</i></td>
<td>

none | manual | auto (default = manual)

As per CSS. (mPDF&nbsp; &gt;= 5.7)</td>
</tr>
<tr>
<td>:nth-child()&nbsp; <span class="smallblock">SELECTOR</span></td>
<td>odd | even | <i>a</i>n+<i>b</i>

As per CSS3 specification</td>
</tr>
<tr>
<td>direction</td>
<td>rtl | ltr (mPDF &gt;= 6.0)</td>
</tr>
</tbody> </table>
<table class="table"> <thead>
<tr> <th>HTML Tag</th>
<td>Property</td>
<td>Values allowed &amp; Notes

</td>
</tr>
</thead> <tbody>
<tr> <th rowspan="7">HR</th>
<td>width</td>
<td><span class="smallblock">LENGTH</span></td>
</tr>
<tr>
<td>text-align</td>
<td>left|right|center</td>
</tr>
<tr>
<td>color</td>
<td><span class="smallblock">COLOR</span></td>
</tr>
<tr>
<td>height</td>
<td>i.e. line-width. <span class="smallblock">LENGTH</span></td>
</tr>
<tr>
<td>margin-top, margin-bottom</td>
<td><span class="smallblock">LENGTH</span></td>
</tr>
<tr>
<td>margin-left, margin-right</td>
<td>auto|0 (only)are supported as an alternative way to align a HR of less than 100% width. Values for margin-left: 0; margin-right: auto; will align the HR to the left etc.</td>
</tr>
<tr>
<td>clear</td>
<td>left|right|both</td>
</tr>
<tr> <th rowspan="18">

IMG

</th>
<td>vertical-align</td>
<td>

top|middle|bottom|baseline|text-bottom|text-top

(Full support only from mPDF 4.2)

</td>
</tr>
<tr>
<td>margin, margin-right, margin-left, margin-top, margin-bottom</td>
<td><span class="smallblock">LENGTH</span></td>
</tr>
<tr>
<td>border, border-right, border-left, border-top, border-bottom</td>
<td>

Must be full declaration of size style and colour e.g.

0.1pt solid|dotted|dashed #cccccc

Will also accept #cccccc 0.1pt solid (which is generated by IE WYSIWYG editor)

and (from mPDF 1.4) solid 3mm #000000

medium | thin | thick accepted for size

</td>
</tr>
<tr>
<td>padding*, padding-right, padding-left, padding-top, padding-bottom</td>
<td><span class="smallblock">LENGTH</span></td>
</tr>
<tr>
<td>background-color</td>
<td><span class="smallblock">COLOR</span>&nbsp; (mPDF &gt;= 5.7.3)<span class="smallblock">&nbsp;</span></td>
</tr>
<tr>
<td>opacity</td>
<td>

Value between 0 and 1.0

CSS3 recommended property (but already supported by FireFox)

Sets the opacity/transparency of the image.

</td>
</tr>
<tr>
<td>image-orientation</td>
<td><span class="smallblock">ANGLE</span> as deg, rad, or grad (as per draft CSS3)&nbsp; mPDF &gt;= 5.1</td>
</tr>
<tr>
<td>image-resolution</td>
<td>normal | [ from-image 

 &lt;dpi&gt; ](as per draft CSS3)&nbsp; mPDF &gt;= 5.1</td>
</tr>
<tr>
<td>image-rendering

</td>
<td>

auto | crisp-edges | optimizequality | smooth&nbsp; (as per draft CSS3)

(mPDF &gt;= 6.0)

Controls whether interpolation is on or off in PDF document. Once set for an image, subsequent use of the same image will use the initial setting for this property.

auto (default) - uses the value set by config variable: $interpolateImages

crisp-edges - interpolation disabled

optimizequality - interpolation enabled

smooth - interpolation enabled

</td>
</tr>
<tr>
<td><i>gradient-mask</i></td>
<td><span class="smallblock">GRADIENT</span>&nbsp; (see notes below)&nbsp; mPDF &gt;= 5.1</td>
</tr>
<tr>
<td>display</td>
<td>none</td>
</tr>
<tr>
<td>visibility</td>
<td>visible | hidden | <i>printonly</i> | <i>screenonly</i>&nbsp; (mPDF &gt;= 5.4)</td>
</tr>
<tr>
<td>transform</td>
<td>

All CSS3 transform functions are supported except matrix() i.e.

translate(), translateX(), translateY()

skew(), skewX(), skewY()

scale(), scaleX(), scaleY()

rotate()

cf. <a href="http://www.w3.org/TR/css3-transforms/#typedef-transform-function">http://www.w3.org/TR/css3-transforms/#typedef-transform-function</a>

</td>
</tr>
<tr>
<td>float</td>
<td>left | right (cf. <a href="{{ "/what-else-can-i-do/images.html" | prepend: site.baseurl }}">Images</a>)

</td>
</tr>
<tr>
<td>z-index</td>
<td>Sets a layer in the PDF document. See <a href="{{ "/what-else-can-i-do/layers.html" | prepend: site.baseurl }}">Layers</a>.</td>
</tr>
<tr>
<td>(vspace, hspace)</td>
<td>Attributes - set values for margin-left/right or margin-top/bottom

</td>
</tr>
<tr>
<td>width, height</td>
<td><span class="smallblock">LENGTH</span>. NB the inline attributes width="" and height="" are also supported</td>
</tr>
<tr>
<td>min-width, min-height, max-width, max-height

</td>
<td><span class="smallblock">LENGTH</span>. (mPDF &gt;= 5.6)

</td>
</tr>
<tr> <th rowspan="3">

SELECT

</th>
<td>font-family</td>
<td><span class="smallblock">FONT-FAMILY</span></td>
</tr>
<tr>
<td>font-size</td>
<td><span class="smallblock">FONT-SIZE</span></td>
</tr>
<tr>
<td>color</td>
<td><span class="smallblock">COLOR</span></td>
</tr>
<tr> <th rowspan="7">TEXTAREA</th>
<td>width, height</td>
<td><span class="smallblock">LENGTH</span>. NB the inline attributes cols="" and rows="" are also supported</td>
</tr>
<tr>
<td>font-family</td>
<td><span class="smallblock">FONT-FAMILY</span></td>
</tr>
<tr>
<td>font-size</td>
<td><span class="smallblock">FONT-SIZE</span></td>
</tr>
<tr>
<td>color</td>
<td><span class="smallblock">COLOR</span></td>
</tr>
<tr>
<td>vertical-align</td>
<td>

top|middle|bottom|baseline|text-bottom|text-top

(Full support only from mPDF 4.2)

</td>
</tr>
<tr>
<td>border-color</td>
<td><span class="smallblock">COLOR</span>&nbsp; Active Forms only (mPDF &gt;= 5.3)</td>
</tr>
<tr>
<td>background-color</td>
<td><span class="smallblock">COLOR</span>&nbsp; Active Forms only (mPDF &gt;= 5.3)</td>
</tr>
<tr> <th>INPUT (type=IMAGE)</th>
<td>width, height</td>
<td><span class="smallblock">LENGTH</span></td>
</tr>
<tr> <th rowspan="5">INPUT (type=BUTTON|SUBMIT|RESET)</th>
<td>font-family</td>
<td><span class="smallblock">FONT-FAMILY</span>&nbsp; Active Forms only (mPDF &gt;= 5.3)</td>
</tr>
<tr>
<td>font-size</td>
<td><span class="smallblock">FONT-SIZE</span>&nbsp; Active Forms only (mPDF &gt;= 5.3)</td>
</tr>
<tr>
<td>color</td>
<td><span class="smallblock">COLOR</span>&nbsp; Active Forms only (mPDF &gt;= 5.3)</td>
</tr>
<tr>
<td>border-color</td>
<td><span class="smallblock">COLOR</span>&nbsp; Active Forms only (mPDF &gt;= 5.3)</td>
</tr>
<tr>
<td>background-color</td>
<td><span class="smallblock">COLOR</span>&nbsp; Active Forms only (mPDF &gt;= 5.3)</td>
</tr>
<tr> <th rowspan="2">INPUT (type=CHECKBOX|RADIO)

</th>
<td>font-size</td>
<td><span class="smallblock">FONT-SIZE</span> (sets size of glyph). Not inherited.

</td>
</tr>
<tr>
<td>color</td>
<td><span class="smallblock">COLOR</span>. Not inherited.</td>
</tr>
<tr> <th rowspan="6">INPUT (type=PASSWORD|TEXT)</th>
<td>width</td>
<td><span class="smallblock">LENGTH</span>. NB the inline attribute size="" is also supported</td>
</tr>
<tr>
<td>font-family</td>
<td><span class="smallblock">FONT-FAMILY</span></td>
</tr>
<tr>
<td>font-size</td>
<td><span class="smallblock">FONT-SIZE</span></td>
</tr>
<tr>
<td>color</td>
<td><span class="smallblock">COLOR</span></td>
</tr>
<tr>
<td>border-color</td>
<td><span class="smallblock">COLOR</span>&nbsp; Active Forms only (mPDF &gt;= 5.3)</td>
</tr>
<tr>
<td>background-color</td>
<td><span class="smallblock">COLOR</span>&nbsp; Active Forms only (mPDF &gt;= 5.3)</td>
</tr>
<tr> <th>BR

</th>
<td>clear

</td>
<td>left|right|both

</td>
</tr>
<tr> <th>DOTTAB</th>
<td><i>outdent</i></td>
<td><span class="smallblock">LENGTH</span>. (mPDF &gt;= 5.7)</td>
</tr>
<tr> <th rowspan="4">

@page

@page &lt;named&gt;&nbsp;

</th>
<td>size</td>
<td>

&lt;length&gt;{1,2} | auto | portrait | landscape

Note: 'em' 'ex' and % are not allowed

Length values are width and height e.g. size: 8.5in 11in; or one value for a square.

Sets the size of the 'page-box', which is usually used with a constant size sheet through the document, as in the CSS2 @paged media spec.

</td>
</tr>
<tr>
<td>sheet-size</td>
<td>

&lt;length&gt;{2} | A4 | A4-L etc.

Note: 'em' 'ex' and % are not allowed

Length values are width and height e.g. size: 8.5in 11in; Any of the standard sheet sizes can be used (as for mPDF() ) with the suffix '-L' for landscape

</td>
</tr>
<tr>
<td>odd-header-name, even-header-name, odd-footer-name, even-footer-name</td>
<td>

A named Header or Footer. HTML headers/footers must precede the name with <span class="parameter">html_</span>

NB This was the original form, and still takes preference over header and footer which can be set using the pseudo-selectors e.g. :right

The name <i>_default</i> can be used to allow the current non-HTML header to remain unchanged (mPDF &gt;= 5.1)

</td>
</tr>
<tr>
<td>margin, margin-left, margin-right, margin-top, margin-bottom</td>
<td><span class="smallblock">LENGTH</span> (% refers to page-box width for left/right, of height for top/bottom)</td>
</tr>
<tr> <th rowspan="11">

@page&nbsp;&nbsp;

@page :right

@page :left

@page :first

@page &lt;named&gt;

</th>
<td>margin-top, margin-bottom</td>
<td>

<span class="smallblock">LENGTH</span> (% refers to page-box width for left/right, of height for top/bottom)

Note that left and right margins cannot be changed when using a page selector.

@page :first is not recognised unless @page has been set with some CSS properties

</td>
</tr>
<tr>
<td><i>margin-header, 

margin-footer</i></td>
<td><span class="smallblock">LENGTH</span></td>
</tr>
<tr>
<td>marks

</td>
<td>

crop | cross | none

From mPDF 5.1 crop and cross can be used together.

</td>
</tr>
<tr>
<td>header, footer</td>
<td>A named Header or Footer. HTML headers/footers must precede the name with <span class="parameter">html_</span> (from mPDF 4.2)</td>
</tr>
<tr>
<td>background, background-image, background-position, background-repeat, background-color</td>
<td>

background is parsed as per the CSS specification.

background-image in the form url(image.png) or url('image.png') supported.

background-position is supported as per CSS2.1

background-repeat: repeat | repeat-x | repeat-y | no-repeat

background-attachment is parsed but has no effect.

See note below. (cf. <a href="{{ "/what-else-can-i-do/backgrounds-borders.html" | prepend: site.baseurl }}">Backgrounds &amp; borders</a>)

</td>
</tr>
<tr>
<td><i>background-image-opacity</i></td>
<td>

Value between 0 and 1.0

Sets the opacity/transparency of the background image.

</td>
</tr>
<tr>
<td><i>background-image-resize</i></td>
<td>0 - No resizing (default)

1 - Shrink-to-fit w (keep aspect ratio)

2 - Shrink-to-fit h (keep aspect ratio)

3 - Shrink-to-fit w and/or h (keep aspect ratio)

4 - Resize-to-fit w (keep aspect ratio)

5 - Resize-to-fit h (keep aspect ratio)

6 - Resize-to-fit w and h

</td>
</tr>
<tr>
<td><i>background-gradient</i></td>
<td>

Defines a linear or radial colour gradient for the background.

linear <span class="smallblock">COLOR1 </span><span class="smallblock">COLOR2</span> x1 y1 x2 y2; or

radial <span class="smallblock">COLOR1 </span><span class="smallblock">COLOR2</span> x1 y1 x2 y2 radius;

x, y and radius are values between 0 and 1

(custom attribute) (cf. <a href="{{ "/what-else-can-i-do/backgrounds-borders.html" | prepend: site.baseurl }}">Backgrounds &amp; borders</a>)

</td>
</tr>
<tr>
<td><i>resetpagenum</i></td>
<td><span class="smallblock">INTEGER</span> Reset page numbering. Use with <b>:first</b></td>
</tr>
<tr>
<td><i>pagenumstyle</i></td>
<td>1 | A | a | I | i&nbsp; <span class="smallblock">&nbsp;</span>See &lt;<a href="{{ "/reference/html-control-tags/pagebreak.html" | prepend: site.baseurl }}">pagebreak</a>&gt; for details</td>
</tr>
<tr>
<td><i>suppress</i></td>
<td>on | off | 1 | 0&nbsp; See &lt;<a href="{{ "/reference/html-control-tags/pagebreak.html" | prepend: site.baseurl }}">pagebreak</a>&gt; for details</td>
</tr>
</tbody> </table>

<b>Common Text Styles</b>

<table class="table"> <tbody>
<tr>
<td rowspan="25">COMMON TEXT STYLES</td>
<td>font-family</td>
<td><span class="smallblock">FONT-FAMILY</span></td>
</tr>
<tr>
<td>font-size</td>
<td>

<span class="smallblock">FONT-SIZE</span>

</td>
</tr>
<tr>
<td>font-style</td>
<td>italic | oblique | normal</td>
</tr>
<tr>
<td>font-weight</td>
<td>bold | normal (only)</td>
</tr>
<tr>
<td>font</td>
<td>Shorthand form, as per CSS2 specification (mPDF &gt;= 4.0)</td>
</tr>
<tr>
<td>font-variant</td>
<td>

normal | none | [ &lt;common-lig-values&gt; 

 &lt;discretionary-lig-values&gt; 

 &lt;historical-lig-values&gt; 

 &lt;contextual-alt-values&gt; 

 historical-forms 

 [ small-caps | all-small-caps | petite-caps | all-petite-caps | unicase | titling-caps ] 

 &lt;numeric-figure-values&gt; 

 &lt;numeric-spacing-values&gt; 

 &lt;numeric-fraction-values&gt; 

 ordinal 

 slashed-zero ]

(mPDF &gt;= 6.0)

</td>
</tr>
<tr>
<td>font-variant-position

</td>
<td>

normal | sub | super

(mPDF &gt;= 6.0)

</td>
</tr>
<tr>
<td>font-variant-caps</td>
<td>

normal | small-caps | all-small-caps | petite-caps | all-petite-caps | unicase | titling-caps

(mPDF &gt;= 6.0)

</td>
</tr>
<tr>
<td>font-variant-ligatures</td>
<td>

normal | none | [ &lt;common-lig-values&gt; 

 &lt;discretionary-lig-values&gt; 

 &lt;historical-lig-values&gt; 

 &lt;contextual-alt-values&gt; ]

(mPDF &gt;= 6.0)

&lt;common-lig-values&gt;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; = [ common-ligatures | no-common-ligatures ]

&lt;discretionary-lig-values&gt; = [ discretionary-ligatures | no-discretionary-ligatures ]

&lt;historical-lig-values&gt;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; = [ historical-ligatures | no-historical-ligatures ]

&lt;contextual-alt-values&gt;&nbsp;&nbsp;&nbsp; = [ contextual | no-contextual ]

</td>
</tr>
<tr>
<td>font-variant-numeric</td>
<td>

normal | [ &lt;numeric-figure-values&gt; 

 &lt;numeric-spacing-values&gt; 

 &lt;numeric-fraction-values&gt; 

 ordinal 

 slashed-zero ]

(mPDF &gt;= 6.0)

</td>
</tr>
<tr>
<td>font-variant-alternates</td>
<td>

Only [normal | historical-forms] supported (i.e. most are NOT supported)

(mPDF &gt;= 6.0)

</td>
</tr>
<tr>
<td>font-language-override</td>
<td>3-letter case-sensitive OpenType language system tag

(mPDF &gt;= 6.0)

</td>
</tr>
<tr>
<td>font-feature-settings</td>
<td>

Comma separated list of &lt;feature-tag-value&gt; with the following syntax:

&lt;feature-tag-value&gt; = &lt;string&gt; [ &lt;integer&gt; | on | off ]?

(mPDF &gt;= 6.0)

</td>
</tr>
<tr>
<td>font-kerning</td>
<td>

auto | normal | none (mPDF &gt;= 5.1)

auto and normal both have the effect of turning kerning on, as long as

<code>$mpdf-&gt;useKerning = true;</code>

</td>
</tr>
<tr>
<td>vertical-align</td>
<td>super | sub | baseline | <span class="smallblock">LENGTH</span>&nbsp; (mPDF &gt;= 5.7.3)</td>
</tr>
<tr>
<td>letter-spacing</td>
<td>normal | <span class="smallblock">LENGTH</span>&nbsp; (mPDF &gt;= 5.1)</td>
</tr>
<tr>
<td>word-spacing</td>
<td>normal | <span class="smallblock">LENGTH</span>&nbsp; (mPDF &gt;= 5.1)</td>
</tr>
<tr>
<td>color</td>
<td><span class="smallblock">COLOR</span></td>
</tr>
<tr>
<td>text-decoration</td>
<td>

underline | line-through | normal (line-through = strike-through)&nbsp; (mPDF &gt;= 5.4)

overline&nbsp; (mPDF &gt;= 5.7.3)

</td>
</tr>
<tr>
<td>text-outline</td>
<td>thickness [ blur ] color; OR none (default)

Blur is not supported.

As per CSS3

(mPDF &gt;= 5.7) Supported in tables &gt;= 6.0

</td>
</tr>
<tr>
<td>text-outline-width, <i>outline-width</i></td>
<td>Width of the outline. <span class="smallblock">LENGTH</span>

(text-outline-width as from mPDF &gt;= 5.7) Supported in tables &gt;= 6.0</td>
</tr>
<tr>
<td>text-outline-color, <i>outline-color</i></td>
<td><span class="smallblock">COLOR</span>&nbsp; = colour of the inner part of the text e.g. #rrggbb. 'INVERT' is also accepted.

(text-outline-color as from mPDF &gt;= 5.7) Supported in tables &gt;= 6.0</td>
</tr>
<tr>
<td>text-shadow</td>
<td>

As per CSS3 specification. 'blur' is not supported.&nbsp; (mPDF &gt;= 5.4)

</td>
</tr>
<tr>
<td>text-transform</td>
<td><span class="smallblock">&nbsp;</span>capitalize | uppercase | lowercase&nbsp; (mPDF &gt;= 5.4)</td>
</tr>
<tr>
<td>unicode-bidi</td>
<td>

normal | embed | isolate | bidi-override | isolate-override | plaintext

(mPDF &gt;= 6.0)

When used on block-level elements:

- the value is not inherited to child blocks

- using "embed" or "isolate" has no effect on block level-boxes

- "isolate-override" is equivalent to "bidi-override" on block-level boxes

</td>
</tr>
</tbody> </table>

<b>Notes:</b>

* Margin, padding, border-width, border-color and border-style accept the various shorthand forms e.g.:

margin:1pt; will set all top, right, bottom and left values the same

margin:1pt 2pt; will set top and bottom to 1pt, left and right to 2pt

margin:1pt 2pt 3pt; will set top to 1pt, left and right to 2pt, and bottom to 3pt (mPDF &gt;= 4.0)

margin:1pt 2pt 3pt 4pt; will set all values in order: top&gt;right&gt;bottom&gt;left

NB Table page-break-inside, autosize values and rotate are only respected for that set on first level table of nested tables

## Border

medium|thin|thick are accepted for size - converted to 1px, 3px, 5px

# See Also

<ul>
<li class="manual_boxlist"><a href="{{ "/what-else-can-i-do/backgrounds-borders.html" | prepend: site.baseurl }}">Backgrounds &amp; Borders (including Gradients)</a></li>
<li class="manual_boxlist"><a href="{{ "/html-support/html-attributes.html" | prepend: site.baseurl }}">HTML supported attributes</a> </li>
</ul>
