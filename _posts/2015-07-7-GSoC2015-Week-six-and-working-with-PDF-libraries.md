---
layout: post
title: GSoC2015 Week six and working with PDF libraries
---

This post is about the progress which I have made while porting print module to Drupal 8 as part of GSoC 2015. Below is an excerpts about the work done in week six while work done in week five can be tracked over <a href="http://zealfire.github.io/Week-five-and-issues-with-PDF-generation/">here</a>.

Last week I had managed to finish work on wkhtmktopdf generator so this week I started to work on mPDF and TCPDF generator. This week was different compared to weeks because midterm evaluation had to be completed about which I was excited in an unusual manner.

The present<strong> printable</strong> module differs a lot from it ancestor module <strong>print</strong> mainly speaking with respect to its current architecture. One of the major changes introduced is keeping a separate module <strong>pdf_api</strong> outside of printable module. So in the present scenario all the preprocessing required before actual PDF to be generated is done in <strong>printable_pdf </strong>module which is a sub module of printable module and all the calling required to function of PDF libraries is done in pdf_api module. So in this way user only need to be majorly aware of one module(printable_module) where configuration settings of PDF is being taken care.

The module is currently making use of repos present at these links <a href="https://github.com/kartik-v/mpdf">mPDF</a> and <a href="https://github.com/tecnickcom/TCPDF">TCPDF</a> to generate PDF. Since this week generators for both mPDF and TCPDF were completed so naturally it was obvious that I was curious as to why we require both of these libraries. On searching a bit I found out on this <a href="http://stackoverflow.com/questions/28696251/why-tcpdf-instead-of-mpdf">link</a> the majpr points in favour of both the libraries.

Some of the major points in favour of TCPDF were that it natively supported SVG format along with text and element strokes while mPDF could be favoured because it fully supported CSS3 hence it rendered far superior quality HTML templates.

The module currently provides user with options like to either save or show inline the PDF, select various page sizes, choose different orientations and set a header and footer. Since the header and footer which are being rendered currently are not configurable right now hence I will be making then configurable next week.Along with that I have planned to write some tests so that module's working status can be verified.     

Some progress of PDF part of  module can be viewed over <a href="https://github.com/zealfire/pdf_api" style="text-decoration:none;" target="_blank">here</a> and remaining over <a href="https://github.com/zealfire/printable/tree/pdf">here</a>. Some of the pull requests made during development can be seen over <a href="https://github.com/zealfire/pdf_api/pulls?q=is%3Apr+is%3Aopen+sort%3Acreated-asc">here</a>. 