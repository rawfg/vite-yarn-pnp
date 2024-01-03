# The problem

The problem is related to the location of the Yarn cache folder on the Windows platform. When the `cacheFolder` setting or `globalFolder` setting when the `enableGlobalCache` is set to `true` (the default behavior) is set to a **different drive than the Vite project** (in this example to `D:\yarn`) there is an error:

```
  VITE v5.0.10  ready in 293 ms

  ➜  Local:   http://localhost:5173/
  ➜  Network: use --host to expose
  ➜  press h + enter to show help
✘ [ERROR] Could not read from file: C:/Users/rawf/projects/vite-yarn-pnp/.yarn/__virtual__/react-dom-virtual-c7b3139f45/6/D:/yarn/cache/react-dom-npm-18.2.0-dd675bca1c-10c0.zip/node_modules/react-dom/client.js
```

I reported a [similar problem](https://github.com/storybookjs/storybook/issues/23497) to Storybook and they fixed it.

# How to reproduce

- Clone this repository
- Use the Yarn _Berry_ version: `yarn set version berry`
- Adapt `.yarnrc.yml` file or set the `globalFolder` setting: `yarn condig set globalFolder D:\yarn`. It doesn't have to be `D` drive but it must be a different drive than the one where project is located.
- Run `yarn` to download depndencies
- Run `yarn dev` to reproduce the issue

