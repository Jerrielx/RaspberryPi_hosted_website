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

<main class="cafe-wrap"> only ONE main per page