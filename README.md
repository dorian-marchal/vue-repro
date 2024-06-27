https://github.com/vuejs/core/issues/11241

## Reproduction

```bash
npm install
# /!\ NODE_ENV=production is important to reproduce the issue
NODE_ENV=production npm run dev
```

Then, click twice on the "toggle expand" button.
You'll get this error in the console:

```
TypeError: Cannot read properties of null (reading 'insertBefore')
    at insert (runtime-dom.esm-bundler.js:16:12)
    at processFragment (runtime-core.esm-bundler.js:4924:7)
    at patch (runtime-core.esm-bundler.js:4442:9)
    at patchKeyedChildren (runtime-core.esm-bundler.js:5549:11)
    at patchChildren (runtime-core.esm-bundler.js:5331:11)
    at patchElement (runtime-core.esm-bundler.js:4760:7)
    at processElement (runtime-core.esm-bundler.js:4599:7)
    at patch (runtime-core.esm-bundler.js:4456:11)
    at patchKeyedChildren (runtime-core.esm-bundler.js:5417:9)
    at patchChildren (runtime-core.esm-bundler.js:5331:11)
```
