# [madlabfau/docker-texlive-full](https://hub.docker.com/r/madlabfau/texlive-full)

This is a Docker image containing a [`TeX Live`](http://en.wikipedia.org/wiki/TeX_Live) installation with many required packages and several fonts.
The goal is to provide a full `Tex Live` installation with all tools and fonts required to do stuff.
We do not use `texlive-full`, but try to emulate it in order to save some space.
Regarding the fonts, we have, e.g., the several pre-installed open Chinese fonts.

Unfortunately, all in all, this makes the container rather big and not very suitable as base image for my other LaTeX-related containers, such as [docker-pandoc](http://www.github.com/thomasWeise/docker-pandoc).
Thus, we now also have a smaller `Tex Live` installation with fewer fonts and utils, namely [docker-texlive-thin](http://www.github.com/thomasWeise/docker-texlive-thin).

## 1. Building and Components

The image has the following components:

- [`TeX Live`](http://www.tug.org/texlive/)
- [`ghostscript`](http://ghostscript.com/)
- [`poppler-utils`](http://poppler.freedesktop.org/)

## 2. License

This image is licensed under the GNU GENERAL PUBLIC LICENSE Version 3, 29 June 2007, which you can find in file [LICENSE.md](http://github.com/thomasWeise/docker-texlive/blob/master/LICENSE.md).
The license applies to the way the image is built, while the software components inside the image are under the respective licenses chosen by their respective copyright holders.

### 3. Utility Scripts

Currently, we provide the following utility scripts in folder `/bin/`:

- `filterPdf.sh <document>` transform a document (either in [PostScript](http://en.wikipedia.org/wiki/PostScript)/`PS`, `EPS`, or `PDF` format) to `PDF` and include as many of the fonts used inside the document into the final `PDF`. This uses ghostscripts `gs` and checks the output with `pdftotext` from `poppler-utils` before replacing `<document>` with the hope to build a final pdf that can display on as many machines correctly as possible.
