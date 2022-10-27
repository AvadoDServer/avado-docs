# avado-docs

The source code for <https://docs.ava.do>

The Avado docs website is build with [Hugo](https://gohugo.io/). You can find installation instructions at <https://gohugo.io/getting-started/installing/>

## Local builds
To test the website locally, run:
```
hugo server
```
By default, this will open a preview build at <http://localhost:1313>

## Theme

The theme is based on [GeekDocs](https://github.com/thegeeklab/hugo-geekdoc).

You can find a demo and the full documentation at <https://geekdocs.de>.


## Authoring tips

* Hint boxes (tip, important):
  * Examples: <https://geekdocs.de/shortcodes/hints/>
  * Code: <https://github.com/thegeeklab/hugo-geekdoc/blob/main/exampleSite/content/en/shortcodes/hints.md>
* Images:
  * Short code: `{{< figure src="surge_strip.jpeg"}}`
  * Parameters: <https://gohugo.io/content-management/shortcodes/#figure>
* Table of Contents:
  * Short code: `{{< toc >}}`
* YouTube
  * Short code: `{{< youtube w7Ft2ymGmfc >}}`
  * Doc: <https://gohugo.io/content-management/shortcodes/#example-youtube-input>
* icon-sets: https://geekdocs.de/features/icon-sets/


### Link checking

Install [Broken-link-checker](https://github.com/stevenvachon/broken-link-checker):
```
npm install broken-link-checker -g
```

Run the checker: (local links only)
```
blc http://localhost:1313 --exclude-external --recursive --ordered
```