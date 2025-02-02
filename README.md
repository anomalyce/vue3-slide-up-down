# vue3-slide-up-down

Like jQuery's [`slideUp`](http://api.jquery.com/slideup/) / [`slideDown`](http://api.jquery.com/slidedown/), but for [Vue 3](vuejs.org)!

Forked from Daniel Diekmeier's [`vue-slide-up-down`](https://github.com/danieldiekmeier/vue-slide-up-down) project.

## Demo

Coming soon

## Installation

```sh
npm i vue3-slide-up-down
```

Usage with Webpack or other module bundlers:

```js
import SlideUpDown from 'vue3-slide-up-down'
// or
const SlideUpDown = require('vue3-slide-up-down')

Vue.component('slide-up-down', SlideUpDown)
```

Or use the UMD build directly in your browser (the component is provided as `window.Vue3SlideUpDown`).

```html
<script
  type="text/javascript"
  src="node_modules/vuejs/dist/vue.min.js"
></script>
<script
  type="text/javascript"
  src="node_modules/vue3-slide-up-down/dist/vue3-slide-up-down.umd.js"
></script>
<script type="text/javascript">
  Vue.component('slide-up-down', Vue3SlideUpDown)
</script>
```

## Usage

The component takes five props:

- `v-model` (Boolean, required): Whether to show the component (`true`) or not (`false`)
- `duration` (Number, optional): How long the animation is supposed to be, in milliseconds. Defaults to `500`.
- `tag` (String, optional): Which HTML tag to use for the wrapper element. Defaults to `div`.
- `use-hidden` (Boolean, optional): Whether to apply the "hidden" attribute to the element when closed. Defaults to `true`. This hides the component from the screen and from assistive devices. The internal elements of the component are completely invisible, and cannot be focused on (by a keyboard or assistive device). (This is probably what you want!) If you need, set this property to `false` to not use the `hidden` attribute. This could be used if you wanted to have a min-height requirement on your component. **⚠️ Note that this can create accessibility issues**, specifically for users with a keyboard or screen reader. Even though the component may _appear_ hidden, focusable elements within the component are still able to be accessed through keyboard navigation.
- `responsive` (Boolean) If true, the container will animate changes in height should the content of the container change (e.g. DOM nodes are added/removed, text content changes ). This will not affect the container if it is closed.

```html
<div class="MyContent">
  <h1>Always show this</h1>

  <slide-up-down v-model="active" :duration="1000">
    Only show this if "active” is true
  </slide-up-down>
</div>
```

The component emits five Vue events:

- `open-start`
- `open-end`
- `close-start`
- `close-end`
- `layout-shift`

```html
<slide-up-down @close-end="console.log('done closing!')" />
```

### Custom `transition-timing-function`

If you want to use a different timing function, add some CSS for your `<slide-up-down>` element.

```html
<style>
  .wobbly-accordion {
    transition-timing-function: cubic-bezier(0.195, 1.65, 0.435, -0.6);
</svtyle>

<slide-up-down class="wobbly-accordion">
  Lorem ipsum dolor sit amet, consectetur adipisicing elit. Soluta omnis velit
  ab culpa, officia, unde nesciunt temporibus cum reiciendis distinctio.
</slide-up-down>
```
