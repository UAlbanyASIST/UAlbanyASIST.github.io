# PostCSS px To em [![Build Status][ci-img]][ci]

[PostCSS] plugin to convert all `px` measurements to `em`.

```css
.foo {
  width: 270px;
  margin: 0 15px;
  padding: 1em;

  /* you can override pixel replacement by adding a "force" *
   * comment after the pixel measurement you want to keep.  */
  border-radius: 10px /*force*/ 16px;
}

@media (min-width: 640px) {
  /* doesn't change pixel values used for media queries, as this wouldn't work properly */
  .foo {
    width: 100%;
    padding: 10px;
  }
}
```

```css
.foo {
  width: 16.875em;
  margin: 0 0.9375em;
  padding: 1em;

  /* you can override pixel replacement by adding a "force" *
   * comment after the pixel measurement you want to keep.  */
  border-radius: 10px /*force*/ 1em;
}

@media (min-width: 640px) {
  /* doesn't change pixel values used for media queries, as this wouldn't work properly */
  .foo {
    width: 100%;
    padding: 0.625em;
  }
}
```

## Rationale

For [Bugherd], we needed to be able to scale our UIs to fit any zoom level on Mobile. To enable this, we change the parents' `font-size` and use `em` measurements relative to the base font size (usually `16px`) in our components. This PostCSS plugin facilitates this, without requiring us to rewrite all our code to use `em` manually.

## Usage

Plug it into your PostCSS configuration.

```js
var options = {
  base: 16, // Base font size; 16px by default
};

// Options may be supplied as the first argument, but are not required.
postcss([require('postcss-px-to-em')(options)])
```

See PostCSS docs for examples for your environment.

[Bugherd]: https://macropod.com/bugherd
[PostCSS]: https://github.com/postcss/postcss
[ci-img]:  https://travis-ci.org/macropodhq/postcss-px-to-em.svg
[ci]:      https://travis-ci.org/macropodhq/postcss-px-to-em
