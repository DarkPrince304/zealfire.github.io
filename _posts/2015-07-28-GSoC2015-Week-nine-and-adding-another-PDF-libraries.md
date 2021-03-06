---
layout: post
title: GSoC2015 Week nine and adding another PDF library
---

This post is about the progress which I have made while porting print module to Drupal 8 as part of GSoC 2015. Below is an excerpts about the work done in week nine while work done in week eight can be tracked over <a href="http://zealfire.github.io/GSoC2015-Week-eight-and-writing-functional-test/">here</a>.

This week I again re-visited PDF generating libraries. And this time I managed to add <strong>dompdf</strong> to PDF submodule. It is an HTML to PDF converter and is compliant with CSS 2.1. The library is available on GitHub over <a href="https://github.com/dompdf/dompdf">here</a> and was easily installed via composer by adding following lines as a requirement in composer.json file of the module:

<code>
{
  
    "require" : {
       "dompdf/dompdf" : "0.6.*"
    }

}
</code>

The library makes use <strong>php-font-lib</strong> hence when we are installing library using composer it is recommended to set parameter <code>DOMPDF_ENABLE_AUTOLOAD</code> defined in the dompdf_config.inc.php file to <code>false</code>. This was done by adding following lines in the generator

<code>
define('DOMPDF_ENABLE_AUTOLOAD', false);

require_once '/path/to/vendor/dompdf/dompdf/dompdf_config.inc.php';
</code> 

After following the above procedure I was finally able to generate PDF for my node's content. It is one of the problem of this library that it does not supports rendering of SVG images but the themes logo which are present in Drupal 8 are of SVG type hence they are not able to render themselves in the PDF. I am still searching a solution for this but currently it seems that the user who wants to have a logo in the PDF will have to themself convert SVG to any other compatible formats like png or GIF. The dompdf generator still lacks function for generating header and footer which I will be adding in coming week.

In this week I was able to add some more unit tests in the module mainly related to testing of configuration of tabs and block generation. The tests can be browsed over <a href="https://github.com/zealfire/printable/tree/master/tests/src/Unit">here</a>. Next week after completing the dompdf generator I will be taking care of some of the loose ends present in the code and then will be adding some more functional tests.

Some progress of PDF part of  module can be viewed over <a href="https://github.com/zealfire/pdf_api" style="text-decoration:none;" target="_blank">here</a> and remaining over <a href="https://github.com/zealfire/printable">here</a>.
