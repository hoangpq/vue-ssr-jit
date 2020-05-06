# vue-ssr-jit

[中文](/README.CN.md)

A just in time compilation technique for server-side rendering. Use the Diff algorithm to derive dynamic and static nodes at runtime, and then generate and run a new rendering tree to dramatically increase rendering performance.

The following vue template: 
```html
<template>
  <div>
    <router-link to="/">{{name}}</router-link>
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: 'vue-ssr-jit'
    }
  }
}
</script>
```

Code generated by the official compiler: 
```js
_c("div", [
  _c("router-link", {attrs: { to: "/" }}, [
    _vm._v(_vm._s(_vm.name))
  ]),
  _c("router-view")
], 1)
```

Code generated using vue-ssr-jit: 
```js
_c("div", [
  _vm._ssrNode(
    "<a href=\"/\" class=\"router-link-active\">vue-ssr-jit</a>"
  ),
  _c("router-view")
], 1);
```

## Use

```js
npm install --save vue-ssr-jit
```

```js
const { createBundleRenderer } = require('vue-ssr-jit')
```

`createBundleRenderer` is consistent with the official function interface of the same name, see the [vue ssr guide](https://ssr.vuejs.org/api/#createbundlerenderer)

It is recommended to use `serverPrefetch` for prefetching data, and it is also supported to use `asyncData` for prefetching data, see [demo](https://github.com/SmallComfort/vue-ssr-jit-demo)

## Implementation principle

[Vue SSR Just In Time Compilation](/PRINCIPLE.md)

## Be careful

This technology is currently in the experimental stage.

## License

[MIT](http://opensource.org/licenses/MIT)
