# FreakyWeb
FreakyWeb but written in FREAK



# [FREAK](https://freaklang.dev/)

## Under development

 Unreleased


---


<div align="center">

<img src="FKWebBanner.png" />

**Web hosting done simple.**

*A lightweight website hosting tool that lets developers share a single layout across plain HTML websites.*

[![License](https://img.shields.io/badge/license-Open%20Source-brightgreen)](https://FreakyWeb.aquaweb.cc/source)
[![Contributions](https://img.shields.io/badge/contributions-open-orange)](https://FreakyWeb.aquaweb.cc/source)

</div>

---

## What is FreakyWeb?

FreakyWeb is a tool that runs a local HTTP server, automatically injecting a shared `template.html` into every page of your static website. Write your content in plain HTML files — FreakyWeb handles the wrapper so you never repeat your navigation, header, or footer again.

---

## Download not yet available!

You're free to compile from source.

---

## Getting Started

### 1 — Required file structure

Your website folder must contain these five files:

```
my-site/
├── index.html          ← Homepage content
├── template.html       ← Shared layout/template
├── notFound.html       ← A page to show for non-existant paths
├── accessDenied.html   ← A page to show for prohibited paths 
└── DeniedPaths.txt     ← A list of prohibited paths, split by new lines
```

### 2 — Set up your layout

`template.html` holds everything that wraps every page: your `<head>` metadata (except `<title>`), navigation, footer, etc. Place the placeholder `<!-- TEMPLATE -->` wherever your per-page content should be injected:

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <!-- shared styles, scripts, meta tags here -->
</head>
<body>
  <nav><!-- your shared nav --></nav>

  <!-- TEMPLATE -->   <!-- page content is injected here [the template comment is replaced] -->

  <footer><!-- your shared footer --></footer>
</body>
</html>
```

### 3 — Write your pages

Each page file only needs a `<head>` tag (for its own `<title>`) and its body content — no `<html>` or `<body>` wrappers needed:

```html
<head>
  <title>About - My Site</title>
</head>

<h1>About Us</h1>
<p>Welcome to my site!</p>
```


### 5 — Restrict access

Add file paths (one per line) to `DeniedPaths.txt` to block those paths from being served to visitors:

```
/DeniedPaths.txt
/admin/secret.html
/internal/config
```

Requests to a denied path are redirected to `accessDenied.html`.

---

## Running the Server

1. Run the program in the directory you want to serve.
2. Set your desired port number.
3. Server running!

---

## How It Works

FreakyWeb uses `Akuma`*(Freak's HTTP server library)* to handle incoming requests. For each `.html` request it:

1. Reads `template.html`
2. Reads the target page file
3. Replaces `<!-- TEMPLATE -->` in the layout with the page content
4. Serves the combined result

Non-HTML files (images, CSS, JS, etc.) are served as raw bytes. Missing pages fall back to a not found page with a `404` status code.

---

## Source Code

The full FREAK source is available in the repository. Contributions are open.

---

## Credits

| Role | Credit |
|------|--------|
| Code & Art/Media | [Akumarin Kukino](https://akumarin.nekoweb.org/) |
| Publisher | Freak Dev Team |


---

<div align="center">

© 2026 Freak Dev Team — FreakyWeb · All code and art/media by Akumarin Kukino

*[Just use HTML.](https://justfuckingusehtml.com/)*

</div>
