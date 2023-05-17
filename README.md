# Snowdog Theme 

A company theme for [Slidev](https://github.com/slidevjs/slidev).

_As this is internal theme I do not intent to publish it on npm as is typical for slidev themes._

## Install

Because this package is not published on npm following rules differ from standard way of working with [sli.dev](https://sli.dev).

### For editing in GitLab

- Fork this repository (make sure it is not Your personal namespace - as namespace with dots in name confuse the heck out of GitLab Pages)
- Edit `example.md`
- Wait for CI/CD Pipeline to finish
- see effect on https://{groupName}.docs.snowdog.pro/{repositoryName} :)

### For local work

- Download contents of this repository
- Copy `example.md` to `slides.md`
- `npm install` to install dependencies 
- `npx slidev` to start service that renders slides and monitors changes
- open [localhost:3030](https://localhost:3030) in browser 
- edit `slides.md` to Your liking

## Layouts

This theme provides the following layouts:

- aboutme - displays name, work position and shows image
- cover - first slide
- intro - on light theme changes background to one with arch
- thankyou - last slide

There are also default layout available

- 404
- center
- cover
- default
- end
- fact
- full
- iframe
- iframe-left
- iframe-right
- image
- image-left
- image-right
- intro
- none
- quote
- section
- statement
- two-cols
- two-cols-header

see [documentation](https://sli.dev/builtin/layouts.html#built-in-layouts) for their description

## Components

This theme provides the following components:

- `<snowdog />` to put snowdog logo on slide (top left or right corner depending on light/dark theme)

## Contributing

- `npm install`
- `npm run dev` to start theme preview of `example.md`
- Edit the `example.md` and style to see the changes
- `npm run export` to generate the preview PDF
- `npm run screenshot` to generate the preview PNG
