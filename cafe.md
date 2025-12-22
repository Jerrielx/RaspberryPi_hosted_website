# cafe notes
# Author: Jerry Cheung
# File: cafe.md
# Date: 2015-12-20
# Description: HTML and CSS learning notes regarding cafe webpage

## HTML part
<!DOCTYPE html> render this page using modern standards mode
<html lang="en"> ... </html> root element of the page, lang accessibility+better SEO, screen readers
<head> ... </head> metadata and resources, not visible page content
<meta charset="UTF-8"/> tells the browser the document is encoded as UTF-8.
<title>...</title> browser tab name, bookmark title
<link rel="stylesheet" hred="cafe.css"> loads css file and applies to html, rel="stylesheet" relationship

<header> semantic(meaning) HTML element, tells browser this is introductory / navigational content of the page
<header> - nav, logo, site identity
<nav> - navigation links, semantic/(meaning) navigation
<main> - main content
<section> - standalone thematic(subject) group of content
<footer> - bottom info
<div> - structural, layout box inside a meaning box

<body> - everything visible on the page
<!-- Comments -->
<header class="cafe-header"> introductory content of the page, adds a label to this header
<div class="cafe-wrap"> generetic container, the wrapped content area with label
<nav class="cafe-nav"> group of links for nagivation and its label
<a class="cafe-brand" href="/cafe">Bistro Gränden</a>
<a> - anchor tag = link, href - destination, /cafe - root of site, class - own label
<a href="#about">About</a> scroll to the element with id="about"

<section class="cafe-hero"> standalone content block about one topic
<div> exists to keep h1 and p together
<h1> only ONE h1 per page, main title of the page
<p> paragraph of text

<main class="cafe-wrap"> this is the primary content of the page, only ONE main per page
<section id="about"> one thematic content block with unique id "about". there can be only one id="about" on the page, target for css or js
<h1> page title, <h2> section titles, <h3> subsections
<br> line break inside text
<footer> sematic block, normally at bottom. behaves like <div>

## CSS part
CSS rule    property: value;
/* comments */ 
Every element in CSS is a box. Box has content, padding, border. outside box: margin
:root{...} pseudo-class selector, selects root element of the document, global variables place
--bg-dark: #27100a; css custom properties(css variables), start with --
how to use: background: var(--bg-dark); use the value stored in --bg-dark

* {} - * means universal selector, select every element on the page
box-sizing: border-box; - width includes content + padding + border
html,body{} apply these rules to both <html> and <body>
scroll-behavior: smooth; clicking <a href="#..."> instead of jumping -> smoothly scrolls
margin - creates space outside the element
padding - pushes content inward. space insite the element

background: background color, images, gradients
color: text color
font-family: tries first font, if not available -> tries the next, keeps going
system-ui->modern system font, -apple-system->macOS/iOS, Segoe UI->windows, Roboto->android, Arial->common fallback, sans-serif->generic fallback

position: sticky; 
top: 0 sets the sticking position: 0px from the top edge
z-index: 50; 
border-bottom: 1px solid rgba(0, 0, 0, .15); adds a think line under the header. 1px width, solid style(continuous line), rgba color(r, g, b, opacity) 

.cafe-wrap{} - any element with class="cafe-wrap"
margin: 0 auto - vertical margin=0, horizontal margin = auto, auto = take leftover horizontal space and split it evenly
padding: 0 24px - 