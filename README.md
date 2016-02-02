<h1>HTML Checklist </h1>

<div>It is enough to check the first 5 items of the list before you deliver a markup to the client. For production, check the first 6 of them.</div>
<div>
<ol>
<li><b>Markup matches the design</b></li>
<li><b>Cross-browser identity, encoding, and DOCTYPE</b></li>
<li><b>Validity (including CSSLint and JSHint), accessibility (ARIA, WCAG), microformats 1 & 2, and microdata</b></li>
<li><b>Independent CSS blocks: cascade minimization, BEM usage</b></li>
<li><b>The site should look good in all the standard resolutions (1024 px and more). There should be no horizontal scroll. The site should fit the screen on mobile devices</b></li>
<li>Correct look after usage of the real text input. Reliability of the markup</li>
<li>CSS should be written using preprocessors (LESS/Sass/Stylus). Preferable usage of build systems (Grunt/Gulp) and postprocessors (PostCSS/Autoprefixer)</li>
<li>Check and optimization of a page loading speed (GTmetrix/Google PageSpeed Insights)</li>
<li>Retina support</li>
<li>Win/Mac/Linux font analogs presence</li>
<li>Accessibility when images are slowly loading or switched off.</li>
<li>HTML5 forms, linking, validation</li>
<li><a href="https://icons8.com/2016/01/27/html-checklist#point13">Proper semantics. Clean HTML and CSS code, consistency, neatness</a></li>
<li>Correct structure of headers (H1, H2, etc. and TITLE)</li>
<li>Operability without (or with not yet loaded) JavaScript</li>
<li>Operability without Flash</li>
<li>Enlarged text causes no bugs</li>
<li><a href="https://icons8.com/2016/01/27/html-checklist#point18">Important little things</a></li>
</ol>
</div>
<a name="point13"></a>
<div><h2>Point 13. Proper Semantics: Good and Bad Practices</h2>
Keep in mind, that semantics can be used in both elements and class names. And BEM class hierarchy is the new level of semantics.

<div><h3>Bad:</h3> 
<ul class="contentListUl">
<li><b>Float: left for all the blocks is the worst thing ever.</b> Fortunately, nowadays it’s less common. If a crazy coder emulates table cells placing blocks one after another like bricks, get him out! It can be checked by Web&nbsp;Developer&nbsp;Outline&nbsp;→&nbsp;Float&nbsp;elements. If red blocks are everywhere, you can throw the code away.</li>
<li>Block indentation should be created by block margin, but not by a margin of the content sticking outside.</li>
<li>The absence of titles is bad. </li>
<li>The absence of <font face="Courier New", "Lucida Console", monospace>img alt= .. </font> is bad. </li>
<li>Hacks for browsers inside main.css are bad (either with or without filters). “Without filters” is if we just type <font face="Courier New", "Lucida Console", monospace>{zoom: 1;}</font>. It is extremely bad because it affects all the IEs, not just the target ones. “With filters” is if we use (<font face="Courier New", "Lucida Console", monospace>* html, *+html,</font> and so on). It is bad again because it spoils the code and makes it less readable. Some hacks can even be invalid and can break CSSLint run. Conditional Comments used to be considered a good practice, but they are bad too. They increase the amount of CSS files and spread the code to different places. Nowadays, it is recommended to use special classes like <font face="Courier New", "Lucida Console", monospace>html.ie7, html.ie8</font>, and so on (from HTML5 Boilerplate). It’s also a good practice to use Modernizr feature detection (classes like <font face="Courier New", "Lucida Console", monospace>html.js.flexbox.canvas.no-touch…</font>) and JS detection of browser and platform (e.g. CSS Browser Selector generating classes like <font face="Courier New", "Lucida Console", monospace>html.webkit.chrome.chrome25.win.win8…</font>).</li>
<li>Not checking forms tabindex is bad.</li>
<li>Writing styles without attention to element placement logic is bad. For instance, if the element is always on the top, it must have a high z-index. If it looks good right now, you can’t be sure it will last forever. Styles have to be rock-solid. If an element has to be on the same place no matter of a surrounding, use <font face="Courier New", "Lucida Console", monospace>position:absolute</font>, but never <font face="Courier New", "Lucida Console", monospace>float</font>. Independent blocks shouldn’t be in the same block together (e.g. company phone number and site search). Placement of independent blocks should be <font face="Courier New", "Lucida Console", monospace>absolute</font>, not <font face="Courier New", "Lucida Console", monospace>float</font>. </li>
<li>Presentational classes (e.g. <font face="Courier New", "Lucida Console", monospace>.right, .red</font>) are very bad.</li>
<li>For a presentational purpose use pseudo-elements instead of empty blocks.</li>
<li>It is bad for standard elements to have no basic styles. In other words, just <font face="Courier New", "Lucida Console", monospace>h1, h2, ul, table</font>, etc. have to look nice without classes. In other words - just use Normalize and not Reset CSS.</li>
<li>Lack of gradual elaboration of text styles is bad. Suppose a style is specified for each element separately but the outer-block element looks totally different. For example, a text without paragraphs can be of an absolutely different style from the rest of the elements in the block. It is good to gradually specify styles upwards from below. It is important not to mix text styles and block styles now. Cascade styling for text is good, but for blocks, it's better to use BEM. </li>
<li>Over detailed global styles are even worse. For example: <br><font face="Courier New", "Lucida Console", monospace>a {font: italic 10px Tahoma;} /* Hate! Hate! Hate!!11 */</font> <br>You will have to redefine the link style for every block afterwards.</li>
<li>Element’s size and positioning should be specified in the same measurement units. Block width/height set in px and margin/padding in em is weird and most likely is a mistake. It is better to set line-height by a coefficient (1, 1.2, 1.4, …). It is an extent to which font-size will be multiplied, and you’ll get line spacing without setting units of measurement. If you have font-size/height in em, then set margin/padding in em, too. It is a classic example of a list <font face="Courier New", "Lucida Console", monospace>dl-dt-dd</font>: <font face="Courier New", "Lucida Console", monospace>dt</font> and <font face="Courier New", "Lucida Console", monospace>dd</font> are placed in front of each other by dragging <font face="Courier New", "Lucida Console", monospace>dd</font> upwards with the negative <font face="Courier New", "Lucida Console", monospace>margin</font> value. Or you can use padding to create a space for some text block with <font face="Courier New", "Lucida Console", monospace>position: absolute</font>. Padding and height of text elements (paragraphs, table cells) should be in em so that font size will be increased correctly.</li>
<li>It is bad (unacceptable!) to put styles on selectors of nested standard tags without classes. Suppose, we have something like 
<font face="Courier New", "Lucida Console", monospace>h2 a span { some tough thing like a picture with graphics, which overlays our header's text}</font> 
And when the user suddenly types the same expression in WYSIWYG form, we get an awesome bug. On the contrary, you can use block <font face="Courier New", "Lucida Console", monospace>.b-text</font> (see BEM) for single text tags displaying from a database. </li>
<li>It is bad to define visual appearance of elements directly through js: <font face="Courier New", "Lucida Console", monospace>$('.element').css(color,"#f00")</font>. It should be done by classes setting/changing.</li>
</ul></div>

<div><h3>Good:</h3>
<ul class="contentListUl">
<li><b>BEM!</b> Important note, it is a methodology, not a tool. It is enough to create ordinary web sites using only BEM CSS without block library and bem-tools. Avoiding cascade is necessary, and BEM is one of the best solutions for that.</li>
<li>Structuring code blocks reflecting document logic is good. You should create div where it’s logically appropriate but presentationally useless. Vice versa try not to put extra div where it is not structure caused and used only for visual effects.</li>
<li><b>HTML5 Boilerplate</b> is a great basic template from "the gurus". You can start using it and join its development. Send your contributions there!</li>
<li>Use existing development solutions, third-party modules, jQuery plugins. Don’t reinvent the wheel. If you decide to reinvent it anyway, then support it, keep your code library up to date (add the new code and update the old one after each project).</li>
<li>Text styles have to be atomic for text blocks, which are edited through an admin panel. Let’s say we have a text block with the structure like this:
<font face="Courier New", "Lucida Console", monospace>.content-text h1
.content-text .entry
.content-text .entry .somenamedblock</font>
In this case <font face="Courier New", "Lucida Console", monospace>.somenamedblock</font> has to get text style directly: <font face="Courier New", "Lucida Console", monospace>.somenamedblock {font: …; color: …;}</font>. Otherwise, we'll be unable to style it in the WYSIWYG editor.</li>
<li>Same html code should be used for blocks with identical content on the front and inner pages. It can be achieved using block and element modifiers, but not through modIfying the parent (e.g. cascade from <font face="Courier New", "Lucida Console", monospace>body.pagename</font>).</li>
</ul></div>
</div>
<a name="point18"></a>
<div><h2>Point 18. Important Little Things</h2>
<ul class="contentListUl">
<li>Logo on the inner pages should be linked to the main page. On the title page logo should be h1. On the insides h1 should be a content header, and Logo should be <font face="Courier New", "Lucida Console", monospace>div</font>.</li>
<li>Each page should have unique TITLE of the format <br><font face="Courier New", "Lucida Console", monospace>About Us — %CompanyName%.</font></li>
<li>All the pages should be interlinked and checked for dead links.</li>
<li>All the links should react on <font face="Courier New", "Lucida Console", monospace>:hover, :active,</font> and <font face="Courier New", "Lucida Console", monospace>:focus</font>. It can be done by showing/removing underline, changing color - anything. All the links should react on <font face="Courier New", "Lucida Console", monospace>:visited</font>, except menu items.</li>
<li>Check all the interactive elements that should work are working.</li>
<li>Content should go at the beginning of the page before any sidebars or other stuff.</li>
<li>All the created pages should be sliced into templates beforehand so that they can be easily integrated by programmers.</li>
<li>Content has to have a proper copyright.</li>
<li>There should be both apple-touch-icon and favicon.ico (better include 32×32, 48×48, and 64×64 versions inside).</li>
<li>There should be no unnecessary comments, unused redundant files, old versions, etc. All the backups can be found in version control system if needed (e.g. Git or SVN). Trash in the living project complicates its development.</li>
<li>Sizes of blocks depending on the text content should be specified in em, not px.</li>
<li>In case if link’s URL is unknown, it should be equal to its anchor spelled in latin characters. Spaces and special characters should be replaced with dashes.</li>
<li>Skype plugin shouldn’t break the markup.</li>
<li>Textarea resizing shouldn’t break it as well.</li>
<li>When checking overall frontend, make sure the response header for a 404 page is 404 and not 200.</li>
<li>It's a good practice to specify sizes of programmatically generated images in CSS.</li>
<li>Check spelling at least in Word, preferably - using special "web-typography" services.</li>
<li>Links to external resources should be with <font face="Courier New", "Lucida Console", monospace>target="_blank"</font>. It’s better to mark them with an icon “external link”.</li>
<li>Of course, images should be placed in a separate folder, css in another one, and js in its own folder, too. Graphics that are not a part of the design (e.g. illustrations, photos in a news, etc.) should be placed in an individual folder e.g. “Userfiles”.</li>
<li>Images should be scalable depending on the window size (<font face="Courier New", "Lucida Console", monospace>max-width:100%; height:auto;</font>).</li>
</ul></div>

<div>Original article by<i> <a href="https://github.com/ihorzenich/html5checklist">Ihor Zenich</a></i>, Frontend Developer at EPAM Systems. </div>
