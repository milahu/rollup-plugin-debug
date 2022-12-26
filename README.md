# rollup-plugin-debug

Code for debugging the flow through rollup plugins. This grew out of an ad hoc solution; I am in the process of breaking it out into an installable NPM module.

## simple debug

```js
// rollup.config.js
export default {
  plugins: [
    thisPlugin(),
    {
      // print filename (id) and code between two plugins
      // https://github.com/rollup/rollup/issues/1215
      transform ( code, id ) {
        console.log( id );
        console.log( code );
        // not returning anything, so doesn't affect bundle
      }
    },
    thatPlugin()
  ],
  // other options
}
```
