---
title: "Adding/Modifying content on Avado-docs"
---

The Avado docs website is built with [Hugo](https://gohugo.io/). You can find installation instructions at <https://gohugo.io/getting-started/installing/>

## Local builds
To test the website locally, run:
```
hugo server
```
By default, this will open a preview build at <http://localhost:1313>

{{< hint type=tip >}}
Run `hugo server --navigateToChanged` to automatically open the pages you are editing
{{< /hint >}}

## Theme

The theme is based on [GeekDocs](https://github.com/thegeeklab/hugo-geekdoc).

You can find a demo and the full documentation at <https://geekdocs.de>.

## Create a new page

Create a new MarkDown page and add following preamble at the start of the file
```
---
title: Create your DApp for the AVADO DAppstore
---
```
You can add a `weight: 30` parameter to influence the position in the table of contents.


[Markdown Cheat Sheet](https://www.markdownguide.org/cheat-sheet/)

## Authoring tips

* Hint boxes (tip, important):
  * Examples: <https://geekdocs.de/shortcodes/hints/>
  * Code: <https://github.com/thegeeklab/hugo-geekdoc/blob/main/exampleSite/content/en/shortcodes/hints.md>
  * Short code: 
```
{{</* hint type=tip title="optional" */>}}
**Markdown content**
Dolor sit, sumo unique argument um no. Gracie nominal id xiv. Romanesque acclimates investiture.
{{</* /hint */>}}
```
* Images:
  * Short code: `{{</* figure src="surge_strip.jpeg" */>}}`
  * Parameters: <https://gohugo.io/content-management/shortcodes/#figure>
  * To add the files: create a folder with the same name as the page and store the images there.
* Table of Contents:
  * Short code: `{{</* toc */>}}`
* YouTube
  * Short code: `{{</* youtube w7Ft2ymGmfc */>}}`
  * Doc: <https://gohugo.io/content-management/shortcodes/#example-youtube-input>
* icon-sets: https://geekdocs.de/features/icon-sets/

### Icons

* https://fontawesome.com/
* https://svgsprit.es/

### Link checking

Install [Broken-link-checker](https://github.com/stevenvachon/broken-link-checker):
```
npm install broken-link-checker -g
```

Run the checker: (local links only)
```
blc http://localhost:1313 --exclude-external --recursive --ordered
```
