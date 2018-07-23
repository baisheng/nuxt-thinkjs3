
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



## Tips
### 非 nuxt 资源的访问
如果希望某些 controller 如 api 不被 nuxt 中间件拦截，请参考下面的代码修改 middleware
```javascript
module.exports = options => {
  let err = null
  const middleware = async (ctx, next) => {
    // 处理不被拦截的路径
    let subdomain = ctx.url.split('/')[1]
    if (subdomain === 'api') {
      return next()
    } else {
      // let isApi
      // 默认访问状态为 404
      ctx.status = 200
      ctx.req.session = await ctx.session()
      await nuxt.render(ctx.req, ctx.res)
      const startTime = Date.now();
      return next().catch(e => {
        err = e
      }).then(() => {
          const endTime = Date.now();
          // nuxt.render(ctx.req, ctx.res)
          if (err) return Promise.reject(err); // 如果后续执行逻辑有错误，则将错误返回
          return new Promise((resolve, reject) => {
            // console.log(`request exec time: ${endTime - startTime}ms`);
          })
        }
      )
    }
  }
  return middleware
}
```
