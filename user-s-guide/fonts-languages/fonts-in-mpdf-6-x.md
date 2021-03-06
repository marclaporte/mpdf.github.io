---
layout: page
title: Fonts in mPDF 6.x
parent_title: Fonts & Languages
permalink: /user-s-guide/fonts-languages/fonts-in-mpdf-6-x.html
---

<div id="bpmbook" class="bpmbook" style="direction:ltr;">
<div class="topic_user_field">
<div id="U0">
<p>mPDF supports Truetype fonts, reading and embedding directly from the .ttf font files. Fonts must follow the Truetype specification and use Unicode mapping to the characters. Truetype collections (.ttc files) and Opentype files (.otf) in Truetype format are also supported.</p>
<h2>Easy to add new fonts</h2>
<ol>
<li>Upload the Truetype font file to the fonts directory (<span class="filename">/ttfonts</span>)</li>
<li>Define the font file details in the configuration file (<span class="filename">config_fonts.php</span>)</li>
<li>Access the font by specifying it in your HTML code as the CSS font-family</li>
<li>To use the font with specific languages, you need also to edit the configuration file (<span class="filename">config_lang2fonts.php</span>) - see the example</li>
</ol>
<h3>Example</h3>
<p>You have 2 font files "Frutiger-Normal.ttf" and "FrutigerObl-Normal.ttf" which you want to be available in mPDF, and you will refer to them in HTML/CSS as "Frutiger".</p>
<p>1. Upload the 2 files to the fonts directory (<span class="filename">/ttfonts</span>)</p>
<p>2. In the configuration file (<span class="filename">config_fonts.php</span>) add this to the array <code>$this-&gt;fontdata</code>:</p>

{% highlight php %}
<?php

&nbsp;&nbsp; "frutiger" =&gt; array(

&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; 'R' =&gt; "Frutiger-Normal.ttf",

&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; 'I' =&gt; "FrutigerObl-Normal.ttf",

&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; ),
{% endhighlight %}

<p>For fonts which handle complex scripts and/or right-to-left text, see <a href="/user-s-guide/fonts-languages/opentype-layout-otl.html">OpenType layout (OTL)</a> for details of setting OTL use and support for kashida e.g.</p>

{% highlight php %}
<?php

&nbsp;&nbsp; "frutiger" =&gt; array(

&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; 'R' =&gt; "Frutiger-Normal.ttf",

&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; 'I' =&gt; "FrutigerObl-Normal.ttf",

&nbsp;&nbsp;&nbsp;&nbsp;<b>&nbsp;&nbsp;&nbsp; 'useOTL' =&gt; 0xFF,</b>

<b>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 'useKashida' =&gt; 75,</b>

&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; ),
{% endhighlight %}

<p>3. In your HTML or CSS code use something like this:</p>

{% highlight php %}
<?php

&lt;p style="font-family: Frutiger"&gt;....&lt;/p&gt;
{% endhighlight %}

<p>4. To use the font with specific languages, you need also to edit the configuration file (<span class="filename">config_lang2fonts.php</span>); let us imagine that Frutiger contains a full set of characters needed for the Thai language:</p>

{% highlight php %}
<?php

&nbsp;&nbsp;&nbsp; &nbsp; // THAI

&nbsp;&nbsp;&nbsp; &nbsp; CASE "th":&nbsp; $unifont = "frutiger";&nbsp; break;
{% endhighlight %}

<p>This will enable the Frutiger font whenever the lang attribute is set, if the configurable variable <code>autoLangToFont</code> is set to <code>true</code>:</p>

{% highlight php %}
<?php

&lt;p lang="th"&gt;...&lt;/p&gt;
{% endhighlight %}

<h2>Full Unicode support</h2>
<p>The DejaVu fonts distributed with mPDF contain an extensive set of characters - see <a href="/reference/codepages-glyphs/unicode-coverage-of-free-fonts.html">Unicode coverage of free fonts</a> for details of these and other open-source fonts.</p>
<h2>Complex scripts</h2>
<h3>Right-to-left languages (Hebrew, Arabic etc.)</h3>
<p>Arabic languages and Hebrew are written in a right-to-left direction (RTL). mPDF recognises both Arabic and Hebrew languages and reverses text direction automatically.</p>
<p class="manual_block">ألسّلام عليكم &nbsp; &nbsp; שלום</p>
<p>Arabic languages (but not Hebrew) also change the form of the letter depending on its position in the text e.g. these are the initial, medial, final, and isolated forms of arabic letter 'ain':</p>
<p class="manual_block">ع ـع ـعـ عـ</p>
<p class="manual_block"><b>Note:</b> You must enable OpenType layout (OTL) features for a font to correctly display right-to-left scripts.</p>
<h3>Indic languages, Lao, Tibetan etc.</h3>
<p>Other complex scripts require some processing of characters before display. For example some vowels consist of 2 characters, to be placed before and after the adjacent consonant e.g.</p>
<p class="manual_block">U+0D1C + U+0D4C [vowel AU] = [written together as &amp;#x0D1C;&amp;#x0D4C;]

ജ + ൌ = ജൌ</p>
<p>Consonant conjuncts are where two adjacent characters are written as a single 'conjunct' form e.g.</p>
<p class="manual_block">प + ॡ = पॣ</p>
<p class="manual_block"><b>Note:</b> You must enable OpenType layout (OTL) features for a font to correctly display complex scripts.</p>
<h3>Vertical writing</h3>
<p>Vertical writing is not supported by mPDF (e.g. Mongolian and Phags-pa) although the individual characters can be displayed using suitable fonts.</p>
<h2>Unicode Supplementary Planes</h2>
<p>The original Unicode allocated characters between x0000 and xFFFF (65,536 characters). This 'Basic Multilingual Plane' supported most characters in common use, including a large number of Unified Chinese-Japanese-Korean characters (CJK). Later the Unicode standard was extended to 16 Planes.</p>
<p>The first plane (plane 0), the Basic Multilingual Plane (BMP), is where most characters have been assigned so far.</p>
<p>Plane 1, the Supplementary Multilingual Plane (SMP), is mostly used for historic scripts such as Linear B, but is also used for musical and mathematical symbols.</p>
<p>Plane 2, the Supplementary Ideographic Plane (SIP), is used for about 40,000 Unified Han (CJK) Ideographs.</p>
<p>mPDF supports fonts containing characters from all Unicode Planes. By choosing the correct font, almost every single character from Unicode 5 can be displayed in a PDF file.</p>
<h3>Unicode Supplementary Multilingual Plane (SMP or Plane 1) U+10000 - U+1FFFF</h3>
<p>The Unicode Supplementary Multilingual Plane contains ranges such as Gothic text and Egyptian Hieroglyphics. as well as other (mainly) ancient scripts - see <a href="/reference/codepages-glyphs/unicode-coverage-of-free-fonts.html">Unicode coverage of free fonts</a> for full list.</p>
<p>mPDF uses a different method to embed fonts in the PDF file if they include characters from SMP or SIP, because the characters cannot be represented by a 4 character hex code 0000-FFFF. This method is less eficient than the default method, and it can be suppressed by adding the font name to the array <code>BMPonly</code> in the <span class="filename">config_fonts.php</span> configuration file.</p>
<p>Note that the DejaVu fonts&nbsp; distributed with mPDF do contain a few characters in the SMP plane, but most users will not require them and by default they are added to the array <code>BMPonly</code>.</p>
<h2>Using CJK fonts in mPDF</h2>
<p>Fonts containing CJK characters are large files, typically 10-30MB. Adobe provides a free download of an 'Asian font pack' allowing you to create PDF files without including (embedding) the font information in the file. This keeps the file size to a minimum and minimises resource usage on your website generating the PDF file. However, users will have to download the Adobe font packs to read the file, and other PDF software will not display the text correctly.</p>
<p>mPDF allows you to embed subsets of CJK fonts keeping file size down, although there is considerable memory usage to generate these files.</p>
<p>Some CJK fonts are broken up into 2 files because of the size of the files. One freely available font with almost complete coverage of all CJK characters (in both BMP and SIP) is 'Sun' available from Alan Wood's excellent website: <a href="http://www.alanwood.net/unicode/fonts-east-asian.html">http://www.alanwood.net/unicode/fonts-east-asian.html</a>. This comes as 2 files, Sun-ExtA and Sun-ExtB (both about 20MB in size) containing the characters from BMP and SIP respectively.</p>
<p>mPDF allows you to treat these as one font by defining the second file as an SIP-extension of the first in the config_fonts.php configuration file.</p>
<p>This is an example of the entry in the <span class="filename">config_fonts.php</span> configuration file:</p>

{% highlight php %}
<?php

$this-&gt;fontdata = array(

...

&nbsp; &nbsp; &nbsp; "sun-exta" =&gt; array(

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'R' =&gt; "Sun-ExtA.ttf",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'sip-ext' =&gt; 'sun-extb',

&nbsp; &nbsp; &nbsp; ),

&nbsp; &nbsp; &nbsp; "sun-extb" =&gt; array(

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 'R' =&gt; "Sun-ExtB.ttf",

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ),

...

);
{% endhighlight %}

<p>This is a sample of HTML code containing CJK characters in both BMP and SIP - note only the sun-exta font-family needs to be referenced:</p>

{% highlight php %}
<?php

&lt;div style="font-family:sun-extA;"&gt; &amp;#40706; &amp;#40712; &amp;#40727; &amp;#x2320f; &amp;#x23225; &amp;#40742; &amp;#40743; &amp;#x2322f; &amp;#x23231; &amp;#40761; &amp;#40772; &amp;#x23232; &amp;#x23233; &amp;#40773; &amp;#40784; &amp;#x23234; &amp;#x23256; &amp;#40787; &amp;#40794; &amp;#x23262; &amp;#x23281; &amp;#40802; &amp;#40809; &amp;#x23289; &amp;#x2328a; &lt;/div&gt;
{% endhighlight %}

<p>&nbsp;</p>
<h2>TrueType Collections</h2>
<p>TrueType Collections (.ttc files) contain more than one font. mPDF treats each font separately by defining the <code>TTCfontID</code> array in the <span class="filename">config_fonts.php</span> configuration file.</p>
<p>This example uses the Windows MingLiU fonts, which consist of 2 files containing 6 fonts (note that mingliub is not a Bold variant):</p>
<p>Font collection file (<span class="filename">mingliu.ttc</span>) contains the following fonts:

[1] MingLiU (mingliu) Regular

[2] PMingLiU (pmingliu) Regular (Proportional)

[3] MingLiU_HKSCS (mingliu_hkscs) Regular</p>
<p>Font collection file (<span class="filename">mingliub.ttc</span>) contains the following fonts:

[1] MingLiU-ExtB (mingliu-extb) Regular

[2] PMingLiU-ExtB (pmingliu-extb) Regular (Proportional)

[3] MingLiU_HKSCS-ExtB (mingliu_hkscs-extb) Regular</p>
<p>&nbsp;</p>
<p>This is the entry in the config_fonts.php configuration file:</p>

{% highlight php %}
<?php

$this-&gt;fontdata = array(

...

&nbsp; &nbsp; &nbsp; "mingliu" =&gt; array(

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'R' =&gt; "mingliu.ttc",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'TTCfontID' =&gt; array (

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'R' =&gt; 1,

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ),

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'sip-ext' =&gt; 'mingliu-extb',

&nbsp; &nbsp; &nbsp; ),

&nbsp; &nbsp; &nbsp; "pmingliu" =&gt; array(

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'R' =&gt; "mingliu.ttc",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'TTCfontID' =&gt; array (

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'R' =&gt; 2,

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ),

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'sip-ext' =&gt; 'pmingliu-extb',

&nbsp; &nbsp; &nbsp; ),

&nbsp; &nbsp; &nbsp; "mingliu_hkscs" =&gt; array(

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'R' =&gt; "mingliu.ttc",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'TTCfontID' =&gt; array (

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'R' =&gt; 3,

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ),

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'sip-ext' =&gt; 'mingliu_hkscs-extb',

&nbsp; &nbsp; &nbsp; ),

&nbsp; &nbsp; &nbsp; "mingliu-extb" =&gt; array(

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'R' =&gt; "mingliub.ttc",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'TTCfontID' =&gt; array (

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'R' =&gt; 1,

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ),

&nbsp; &nbsp; &nbsp; ),

&nbsp; &nbsp; &nbsp; "pmingliu-extb" =&gt; array(

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'R' =&gt; "mingliub.ttc",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'TTCfontID' =&gt; array (

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'R' =&gt; 2,

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ),

&nbsp; &nbsp; &nbsp; ),

&nbsp; &nbsp; &nbsp; "mingliu_hkscs-extb" =&gt; array(

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'R' =&gt; "mingliub.ttc",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'TTCfontID' =&gt; array (

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'R' =&gt; 3,

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ),

&nbsp; &nbsp; &nbsp; ),

...

);
{% endhighlight %}

<p>This is an example of HTML code containing CJK characters from both BMP and SIP, and selecting the different fonts:</p>

{% highlight php %}
<?php

&lt;div style="font-family:mingliu;"&gt; &amp;#40706; &amp;#40742; &amp;#40772; &amp;#40784; &amp;#40802; &amp;#40809; &amp;#x23289; &amp;#x2328a; &lt;/div&gt; 

&lt;div style="font-family:mingliu_hkscs;"&gt; &amp;#40706; &amp;#40742; &amp;#40772; &amp;#40784; &amp;#40802; &amp;#40809; &amp;#x23289; &amp;#x2328a; &lt;/div&gt; 

&lt;div style="font-family:pmingliu;"&gt; &amp;#40706; &amp;#40742; &amp;#40772; &amp;#40784; &amp;#40802; &amp;#40809; &amp;#x23289; &amp;#x2328a; &lt;/div&gt;
{% endhighlight %}

</div>
</div>

