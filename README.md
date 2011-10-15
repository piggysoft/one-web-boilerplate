# One Web/Mobile First Responsive Boilerplate


## What is it? 

The One Web Frontend Boilerplate is a modular framework for building responsive 
websites with Apache Server Side Includes: http://httpd.apache.org/docs/2.2/howto/ssi.html.

It draws code from many other projects, combining various solutions into a custom, 
modular frontend framework (please see Credits section below). The project also 
includes Ant build script that runs code quality tools against JavaScript and 
CSS files, minifying and concatenating them at the end of the process. 

There's nothing really new in this boilerplate, but it works well for me which is 
why I'm publishing it. It builds on many of the best practices found in the resources 
listed under Credits. It basically extends popular boilerplates with Server Side 
Includes. The goal is to achieve a modular and responsive frontend build 
environment, following industry best practices. The framework can be plugged 
into Continuous Integration solutions, such as Jenkins: http://jenkins-ci.org. 


## File structure

### There are two main directories: /build and /webroot.

* /build contains Ant build script and all the tools you need to make your frontend build. Build properties are defined in /build/config/default.properties.

* /webroot contains two subdirectories: /assets and /html. 

* /webroot/assets contains all the stylesheets, JavaScript files and theme images. 

* /webroot/html contains all the HTML files, generated by Apache Server Side Includes. HTML properties are defined in config.shtml in the root.


## Build tools

* Ant 
* YUI Compressor
* Rhino
* JSLint
* JSHint
* CSSLint
* JSDoc Toolkit


## Things you need to know

* Media Queries are based on 16px default font size and defined in ems.
  If you don't go for responsive design (you should!), just remove 
  /webroot/assets/css/responsive.css. The framework is designed to be modular so 
  if you only want to build a desktop site (you shouldn't!) you can split your 
  layout into modules, and place the styles in /webroot/assets/css/modules. 
  You decide.

* JavaScript should not be relied on for layout. That's why I'm using the following 
  method, adopted from Nicholas Zakas and Tantek Çelik: 
  http://www.nczonline.net/blog/2011/03/22/using-html5-semantic-elements-today/, http://tantek.com/presentations/2010/11/html5-now/

  Example:
  <section><div class="section content"></div></section>

  Styles: 
  .content {}

* Don’t use IDs in CSS selectors. Use classes, or ARIA landmark roles instead 
  (referenced with CSS attribute selectors). See also http://oli.jp/2011/ids/.

* CSSLint is currently not used. I find it way too strict and it's still buggy 
  (it complains about Media Queries, for example). I'll plug it in the build 
  script once these issues have been resolved. 

* I'm using Sticky footer solution: http://www.cssstickyfooter.com.


## Logic

### HTML
* Each page has a controller in /webroot/html/pages/pagename/index.shtml.
  In that file, we include the config file and set variables, define the view, and 
  template file that we need to include, to render that particular page.

### CSS - five stylesheets by default, included in the following order: 
* /webroot/assets/css/normalize.css (reset styles)
* /webroot/assets/css/base.css (global, mobile first styles, containing only common colour and typographic rules for basic experience to all users)
* /webroot/assets/css/responsive.css (Add layout with Media Queries for responsive, enhanced design for smartphones, tablets and larger screens)
* /webroot/assets/css/utilities.css (helper styles from HTML5 Boilerplate and HTML5 Mobile Boilerplate)
* /webroot/assets/css/ie/ie6.1.1.css (Universal IE6 styles, not concatendated with other styles)

Any other stylesheets you create should be placed in /modules. Remember to update references in /html/components/document_head.shtml. 
After the base styles, the order in which the module stylesheets are included should't matter (you write your styles carefully, right?)
The idea is that module styles inherit only from base rules, not from other modules. 

### JavaScript
* Third-party plugins are included in /webroot/assets/js/lib. Custom scripts are in /webroot/assets/js.


## Credits

### Boilerplates:
* http://html5boilerplate.com
* http://html5boilerplate.com/mobile
* http://forabeautifulweb.com/blog/about/320_and_up/
* Archetype framework: Will Howat (@willhowat: http://twitter.com/willhowat) and Andrew Massey (@wearymadness: http://twitter.com/wearymadness). It's all because of them. Thanks guys! 

### Solutions:
* http://code.google.com/chrome/chromeframe/
* http://www.cssstickyfooter.com/

### Media queries:
* http://forabeautifulweb.com/blog/about/hardboiled_css3_media_queries/
* http://stuffandnonsense.co.uk/blog/about/proportional_leading_with_css3_media_queries/
* http://www.blog.highub.com/mobile-2/revisit-hardboiled-css3-media-queries/
* http://css-tricks.com/6731-css-media-queries/
* http://www.quirksmode.org/blog/archives/2010/08/combining_media.html
* http://www.slideshare.net/bryanrieger/rethinking-the-mobile-web-by-yiibu
* http://www.cloudfour.com/css-media-query-for-mobile-is-fools-gold/
* http://www.broken-links.com/2011/02/21/using-media-queries-in-the-real-world/

### Inspiration:
* http://www.abookapart.com/products/responsive-web-design
* http://easy-readers.net/
* http://www.alistapart.com/articles/responsive-web-design/
* http://www.lukew.com/ff/entry.asp?933
* http://adactio.com/journal/1716/
* http://adactio.com/journal/4780/
* http://adactio.com/journal/1700/

### Markup:
* http://www.456bereastreet.com/archive/201103/html5_sectioning_elements_headings_and_document_outlines/
* http://www.456bereastreet.com/archive/201104/html5_document_outline_revisited/
* http://mezzoblue.com/archives/2011/01/31/boilerplate/
* http://www.nczonline.net/blog/2011/03/22/using-html5-semantic-elements-today/
* http://tantek.com/presentations/2010/11/html5-now/
* http://microformats.org/wiki/hatom

### Images:
* http://unstoppablerobotninja.com/entry/fluid-images/
* http://www.cloudfour.com/responsive-imgs-part-2/

### CSS:
* http://oli.jp/2011/ids/
* http://code.google.com/p/universal-ie6-css/
* https://github.com/necolas/normalize.css

### JavaScript:
* http://labjs.com/

**There's no mobile, everything's mobile.**

(TO-DO: Add Ant build documentation)

