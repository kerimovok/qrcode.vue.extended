# qrcode.vue

⚠️ Now when you are using Vue 3.x, please upgrade `qrcode.vue` to `3.x`

🔒 if you are using Vue 2.x, please keep using version `1.x`;

A Vue.js component to generate [QRCode](https://en.wikipedia.org/wiki/QR_code). Both support Vue 2 and Vue 3.

[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/scopewu/qrcode.vue/blob/master/LICENSE)

[中文](./README-zh_cn.md)

## install

the `qrcode.vue` component can use in you Vue.js app.

```bash
npm install --save qrcode.vue # yarn add qrcode.vue
```

```
dist/
|--- qrcode.vue.cjs.js         // CommonJS
|--- qrcode.vue.esm.js         // ES module
|--- qrcode.vue.browser.js     // UMD for browser or require.js or CommonJS
|--- qrcode.vue.browser.min.js // UMD Minimum size
```

## Usage

e.g.

```javascript
import { createApp } from 'vue'
import QrcodeVue from 'qrcode.vue'

createApp({
  data: {
    value: 'https://example.com',
  },
  template: '<qrcode-vue :value="value"></qrcode-vue>',
  components: {
    QrcodeVue,
  },
}).mount('#root')
```

Or single-file components with a `*.vue` extension:

```html
<template>
  <qrcode-vue :value="value" :size="size" level="H" />
</template>
<script>
  import QrcodeVue from 'qrcode.vue'

  export default {
    data() {
      return {
        value: 'https://example.com',
        size: 300,
      }
    },
    components: {
      QrcodeVue,
    },
  }
</script>
```

When you use the component with Vue 3 with `TypeScript`:

```html
<template>
  <qrcode-vue :value="value" :level="level" :render-as="renderAs" />
</template>
<script setup lang="ts">
  import { ref } from 'vue'
  import QrcodeVue from 'qrcode.vue'
  import type { Level, RenderAs } from 'qrcode.vue'

  const value = ref('qrcode')
  const level = ref<Level>('M')
  const renderAs = ref<RenderAs>('svg')
</script>
```

### Example Usage With Gradient

To use the `QrcodeVue` component with gradient support, you can pass the gradient-related props:

```html
<template>
  <qrcode-vue
    :size="size"
    :value="fullUrl"
    :level="level"
    :margin="margin"
    :render-as="renderAs"
    :background="background"
    :gradient="true"
    :gradient-type="gradientType"
    :gradient-start-color="gradientStartColor"
    :gradient-end-color="gradientEndColor"
  />
</template>

<script>
export default {
  data() {
    return {
      size: 200,
      fullUrl: 'https://example.com',
      level: 'H',
      margin: 4,
      renderAs: 'svg', // or 'canvas'
      background: '#ffffff',
      gradient: true,
      gradientType: 'linear', // or 'radial'
      gradientStartColor: '#ff0000', // Start color of the gradient
      gradientEndColor: '#0000ff', // End color of the gradient
    }
  },
}
</script>
```

## Component props

### `value`

- Type: `string`
- Default: `''`

The value content of qrcode.

### `size`

- Type: `number`
- Default: `100`

The size of qrcode element.

### `render-as`

- Type: `RenderAs('canvas' | 'svg')`
- Default: `canvas`

Generate QRcode as `canvas` or `svg`. The prop `svg` can work on SSR.

### `margin`

- Type: `number`
- Default: `0`

Define how much wide the quiet zone should be.

### `level`

- Type: `Level('L' | 'M' | 'Q' | 'H')`
- Default: `H`

qrcode Error correction level (one of 'L', 'M', 'Q', 'H'). Know more, [wikipedia: QR_code](https://en.wikipedia.org/wiki/QR_code#Error_correction).

### `background`

- Type: `string`
- Default: `#ffffff`

The background color of qrcode.

### `foreground`

- Type: `string`
- Default: `#000000`

The foreground color of qrcode.

### `gradient`

- Type: `boolean`
- Default: `false`

Enable gradient fill for the QR code.

### `gradient-type`

- Type: `GradientType('linear' | 'radial')`
- Default: `linear`

Specify the type of gradient.

### `gradient-start-color`

- Type: `string`
- Default: `#000000`

The start color of the gradient.

### `gradient-end-color`

- Type: `string`
- Default: `#ffffff`

The end color of the gradient.

### `class`

- Type: `string`
- Default: `''`

The class name of qrcode element.

## License

copyright &copy; 2021 @scopewu, license by [MIT](https://github.com/scopewu/qrcode.vue/blob/master/LICENSE)
