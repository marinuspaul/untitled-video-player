# Untitled Video Player

This is a very simple web-based videoplayer. It provides a netflix-like interface where users can select between different films based on their covers and watch them in a fullscreen player.

As it was designed for a exhibition, it is as simple as possible without any distracting elements that are not needed in this context.

![Video Player Example](./untitled-video-player-screenshot.png)

## How does it work?

The system is based on [Astro](https://astro.build/) and can be easily filled with your content, built and run wherever you want. Apart from the videos itself and their corresponding posters you can provide additional data like the title and authors of each film.

The player itself is based on [video.js](https://videojs.com/)

## Features

- Main menu to select films based on their posters
- Automatic fullscreen player
- Overlay for player, showing additional information for each film
- Autoplay
- Structure films into different collections
- Customizable text for UI elements

## How to use:

Please note that this is a personal project made public. You are free to use it and modify it however you like, but as it was developed for a special use case, it is very likely you need to adapt quite a few things to your needs.

### 1. Clone or download repository

### 2. Install dependencies

```console
$ npm i
```

### 3. Provide your data

You can provide your films and posters by simply dropping them in the `public` folder.
The ideal resolution for the posters is 707px × 1000px and they should be in `.webp` format.
For best browser support the films should be in `.mp4` format.

You also need to create a corresponding markdown file for each movie in the `src/content/films` directory.
Make sure to give them all matching file names and your films should now show up in the interface.

In the end the file structure should look something like this:

```text
/
├── public/
│   ├── films/
│   │   ├── super-cool-movie.mp4
│   │   └── …
│   └── posters/
│       ├── super-cool-movie.webp
│       └── …
├── src/
│   ├── content/
│   │   ├── films/
│   │   │   ├── super-cool-movie.md
│   │   │   └── …
│   │   …
│   …
…
```

### 4. Add additional information

You can provide additional Information for each film in the frontmatter of their markdown files. Currently the properties `title` and `author` are supported.

**src/content/films/super-cool-movie.md:**

```markdown
---
title: Super Cool Movie
author: Quentin Tarantino
---
```

### 5. Structure your content

The films can be grouped into different sections by creating a markdown file for each section in the `content/sections` directory. You then need to provide an `id` for each section and give all the films, that belong in a section the same `sectionID`:

**src/content/sections/example-section.md:**

```markdown
---
title: This is a section
subtitle: Section Subtitle
id: example-section
---
```

**src/content/films/super-cool-movie.md:**

```markdown
---
title: Super Cool Movie
author: Quentin Tarantino
sectionID: example-section
---
```

### 6. Customize player

You can customize UI labels and the main title on the top of the interface by changing the properties of the files in the `content/ui` directory.

### 7. Run dev server to test

To check if everything is working properly just start the dev server at any time:

```console
$ npm run dev
```

### 6. Build

```console
$ npm run build
```

Builds your player into the `dist` directory.

### 7. Run

You can now run the contents of your `dist` directory on any server or just start a local webserver, which was the most handy solution for me as I only needed to run it on a few machines for an exhibition.

## Notes

Autoplay does not work by default in Safari. It needs to be enabled under “Settings > Websites”
