
# Nuxt.js with ThinkJS

> [ThinkJS](https://thinkjs.org/) + [Nuxt.js](https://nuxtjs.org) = :zap:

## Installation

```bash
npm install # or yarn install*[see note below]
```

> Make sure to use a version of vue-cli >= 2.1 (vue -V).

*Note: Due to a bug in yarn's engine version detection code if you are
using a prerelease version of Node (i.e. v7.6.0-rc.1) you will need to either:

  1. Use `npm install`
  2. Run `yarn` with a standard release of Node and then switch back

## Commands

| Command | Description |
|---------|-------------|
| npm start | Start ThinkJs server in development. |

## Deploy with pm2

Use pm2 to deploy app on production enviroment.

```
pm2 startOrReload pm2.json
```

## Documentation

- [ThinkJS](https://thinkjs.org/)
- [Nuxt.js](https://nuxtjs.org/guide/)
- [Vue.js](http://vuejs.org/guide/)

## Licenses

- [TthinkJS license](https://github.com/thinkjs/thinkjs/blob/master/LICENSE)
- [NuxtJS license](https://github.com/nuxt/nuxt.js/blob/master/LICENSE.md)
- [VueJS license](https://github.com/vuejs/vue/blob/master/LICENSE)


