# SlideCore

A small, dependency-free carousel engine for vanilla JS. One constructor, a
plain options object, and the exact behavior you ask for — looped, paged,
autoplaying, or plain.

**[Live demo](https://qimimasterd.github.io/SlideCore/)** · Built and maintained by [@qimiMasterD](https://github.com/qimiMasterD)

## Features

- Zero dependencies, no build step required
- Show any number of items per view (`items`)
- Move by a custom step or by full "pages" (`slideBy`)
- Optional infinite looping with seamless clone-based wraparound (`loop`)
- Optional autoplay with hover-to-pause (`autoplay`, `autoplayHoverPause`)
- Auto-generated prev/next buttons and pagination dots, or wire up your own
  elements (`prevButton`, `nextButton`)

## Install

### CDN (jsDelivr)

Serves straight from the GitHub repo — no publish step needed.

```html
<link
    rel="stylesheet"
    href="https://cdn.jsdelivr.net/gh/qimiMasterD/SlideCore@1.0.0/SlideCore.min.css"
/>
<script src="https://cdn.jsdelivr.net/gh/qimiMasterD/SlideCore@1.0.0/SlideCore.min.js"></script>
```

### GitHub

```bash
git clone https://github.com/qimiMasterD/SlideCore.git
```

Or grab a specific version from the [tags page](https://github.com/qimiMasterD/SlideCore/tags).

## Quickstart

```html
<!-- 1. Wrap your slides in a container -->
<div id="slide">
    <div>Slide 1</div>
    <div>Slide 2</div>
    <div>Slide 3</div>
</div>

<!-- 2. Link the library -->
<link rel="stylesheet" href="./src/SlideCore.css" />
<script src="./src/SlideCore.js"></script>

<!-- 3. Construct it -->
<script>
    const mySlider = new SlideCore("#slide", {
        items: 1,
        loop: true,
        autoplay: true,
    });
</script>
```

## Options

### Layout

| Option    | Default | Description                                                                           |
| --------- | ------- | ------------------------------------------------------------------------------------- |
| `items`   | `1`     | Number of slides visible in the viewport at once.                                     |
| `slideBy` | `1`     | Slides moved per navigation click. Pass `"page"` to move by however many are visible. |

### Motion

| Option               | Default | Description                                                   |
| -------------------- | ------- | ------------------------------------------------------------- |
| `speed`              | `300`   | Transition duration in milliseconds when the slide changes.   |
| `loop`               | `false` | Wraps back to the first slide after the last, and vice versa. |
| `autoplay`           | `false` | Advances the slider automatically without user input.         |
| `autoplayTimeout`    | `3000`  | Delay in milliseconds between automatic transitions.          |
| `autoplayHoverPause` | `true`  | Pauses autoplay while the pointer is over the carousel.       |

### UI

| Option                      | Default      | Description                                                                        |
| --------------------------- | ------------ | ---------------------------------------------------------------------------------- |
| `nav`                       | `true`       | Shows pagination dots below the carousel.                                          |
| `controls`                  | `true`       | Shows previous/next buttons.                                                       |
| `controlsText`              | `["<", ">"]` | Label or HTML rendered inside the auto-generated prev/next buttons.                |
| `prevButton` / `nextButton` | `null`       | Selector for your own button elements, if you'd rather not use the generated ones. |

## Methods

| Method            | Description                                                                  |
| ----------------- | ---------------------------------------------------------------------------- |
| `moveSlide(step)` | Moves the slider by `step` positions. Pass a negative number to go backward. |

```js
mySlider.moveSlide(1); // next
mySlider.moveSlide(-1); // previous
```

## Examples

**Basic, single slide**

```js
new SlideCore("#slide", {
    items: 1,
});
```

**Multi-item, looped, autoplaying**

```js
new SlideCore("#slide", {
    items: 2,
    loop: true,
    slideBy: 2,
    autoplay: true,
    autoplayTimeout: 1500,
    autoplayHoverPause: true,
});
```

**Custom buttons, no dots**

```js
new SlideCore("#slide", {
    items: 1,
    nav: false,
    prevButton: "#my-prev",
    nextButton: "#my-next",
});
```

More live, working configurations are in [`index.html`](./index.html).

## Project structure

```
SlideCore/
├── index.html          # demo / landing page
├── src/
│   ├── SlideCore.js     # library source
│   └── SlideCore.css    # core layout styles (theme-agnostic)
└── assets/
    └── style.css        # demo page theme, not required to use the library
```

## Browser support

Any browser with Flexbox and ES6 class support. No polyfills included.

## License

MIT
