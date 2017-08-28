# vue-proxy

开发`vue.js`的项目时，开发环境下通过代理访问后台服务，生成环境则直接把静态页面文件放在所在`http`服务上。本项目是基于`vue-cli`，后台使用已有的一个[demo](https://github.com/tadashi-chen/express-demo)，实际开发中可以是其他的服务器，如`tomcat`、`iis`等

#### 主要配置

```javascript
module.exports = {
  dev: {
    proxyTable: {
      '/api': {
        target: 'http://192.168.191.1:4000',
        changeOrigin: true,
        // pathRewrite: {
        //   '^/api': '/api'
        // }
      }
    }
  }
}
```

#### 前端访问

```javascript
methods: {
  get () {
    this.$http.get('/api/ajax', { params: { sendMsg: 'Get request here' } }).then(
      (r) => {
        if (r.body.msg) {
          this.$el.querySelector('div[name=result]').innerText = r.body.msg;
        }
      },
      (r) => {
        console.log('fail');
      }
    )
  }
}
```

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```
