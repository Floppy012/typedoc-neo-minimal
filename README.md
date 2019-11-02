# typedoc-neo-theme bug showcase

Issue: [https://github.com/google/typedoc-neo-theme/issues/15](https://github.com/google/typedoc-neo-theme/issues/15)

This is a minimal repo for showcasing a bug when using `typedoc-neo-theme:1.0.3` in combination with `typedoc:0.15.0`

## Replicate

* `npm install`
* `npm run docs`

... should give you this error:

```
$ npm run docs

> typedoc-neo-minimal@1.0.0 docs /tmp/test
> npm run clean && typedoc --theme ./node_modules/typedoc-neo-theme/bin/default/ --out docs --module node ./src/


> typedoc-neo-minimal@1.0.0 clean /tmp/test
> rm -rf ./docs/

Error: The plugin /tmp/test/node_modules/typedoc-neo-theme could not be loaded.

Error: Cannot find module '@gerrit0/typedoc/dist/lib/converter/components'
Require stack:
- /tmp/test/node_modules/typedoc-neo-theme/bin/default/plugin.js
- /tmp/test/node_modules/typedoc-neo-theme/index.js
- /tmp/test/node_modules/typedoc/dist/lib/utils/plugins.js
- /tmp/test/node_modules/typedoc/dist/lib/utils/index.js
- /tmp/test/node_modules/typedoc/dist/lib/serialization/components.js
- /tmp/test/node_modules/typedoc/dist/lib/serialization/index.js
- /tmp/test/node_modules/typedoc/dist/lib/application.js
- /tmp/test/node_modules/typedoc/dist/lib/cli.js
- /tmp/test/node_modules/typedoc/bin/typedoc
    at Function.Module._resolveFilename (internal/modules/cjs/loader.js:794:15)
    at Function.Module._load (internal/modules/cjs/loader.js:687:27)
    at Module.require (internal/modules/cjs/loader.js:849:19)
    at require (internal/modules/cjs/helpers.js:74:18)
    at /tmp/test/node_modules/typedoc-neo-theme/bin/default/plugin.js:33:26
    at /tmp/test/node_modules/typedoc-neo-theme/bin/default/plugin.js:9:17
    at Object.<anonymous> (/tmp/test/node_modules/typedoc-neo-theme/bin/default/plugin.js:15:3)
    at Module._compile (internal/modules/cjs/loader.js:956:30)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:973:10)
    at Module.load (internal/modules/cjs/loader.js:812:32)

Using TypeScript 3.5.3 from /tmp/test/node_modules/typescript/lib
Rendering [========================================] 100%
Error: Documentation could not be generated due to the errors above.
```

## Expected Behaviour

The docs should build without any error.

* `rm -rf node_modules/`
* `git checkout expected`
* `npm install`
* `npm run docs`

... should give you this output:

```
$ npm run docs

> typedoc-neo-minimal@1.0.0 docs /tmp/test
> npm run clean && typedoc --theme ./node_modules/typedoc-neo-theme/bin/default/ --out docs --module node ./src/


> typedoc-neo-minimal@1.0.0 clean /tmp/test
> rm -rf ./docs/

Loaded plugin /tmp/test/node_modules/typedoc-neo-theme

Using TypeScript 3.5.3 from /tmp/test/node_modules/typescript/lib
Rendering [========================================] 100%

Documentation generated at /tmp/test/docs
```
