# rollup-plugin-debug

Code for debugging the flow through rollup plugins. This grew out of an ad hoc solution; I am in the process of breaking it out into an installable NPM module.

## simple debug

you may not need `rollup-plugin-debug` ...

```js
// rollup.config.js

function printFilesPlugin(label = "") {
  let fileIndex = 0;
  return {
    // print filePath and code between two plugins
    // https://github.com/rollup/rollup/issues/1215
    transform(code, filePath) {
      const prefix = label ? (label + ": ") : ""
      console.log(prefix + "-------------------------------------");
      console.log(prefix + fileIndex + ": " + filePath);
      console.log(code.split("\n").map((line, lineIndex) => prefix + fileIndex + ": " + lineIndex + ": " + line).join("\n"));
      fileIndex++;
      // return undefined = no change
    }
  }
}

export default {
  plugins: [
    thisPlugin(),
    printFilesPlugin("this-that"),
    thatPlugin()
  ],
  // other options
}
```
