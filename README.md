# rollup-plugin-debug

Code for debugging the flow through rollup plugins. This grew out of an ad hoc solution; I am in the process of breaking it out into an installable NPM module.

## simple debug

```js
// rollup.config.js

const printFilesPlugin = {
  // print filename (id) and code between two plugins
  // https://github.com/rollup/rollup/issues/1215
  transform(code, id) {
    console.log(id);
    console.log(code);
    // return undefined = no change
  }
};

export default {
  plugins: [
    thisPlugin(),
    printFilesPlugin,
    thatPlugin()
  ],
  // other options
}
```
