# cnode2

> 练手啦

> [样式就不写啦 sass](https://www.sass.hk/)

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
> 配置中修改  config/index.js dev --> proxyTable
通过配置代理解决axios跨域
proxyTable: {
  '/api/v1/**': {
      target: 'https://cnodejs.org',
      secure: false,
      changeOrigin: false
  }
}, 

productionSourceMap: true, // 是否生成.map文件

> 附 standard标准风格规范说明
1. 缩进使用两个空格
2. 字符串使用单引号，用双引号只是为了避免转义单引号
3. 无未使用变量。即定义变量必须使用
4. 不使用分号
5. 行首不能是(,[,`  (省略分号造成的)
6. 关键字后面放一个空格
7. 函数名字后面放一个空格
8. 始终用 === ，不要用 == 。不过可以使用obj == null 检测 null || undefined
9. 始终处理node.js回调的err参数
10. 始终以window引用浏览器的全局变量。document和navigator除外。
11. 某一行禁用所有的规则
    var = '34'; // eslint-disable-line
    只禁用 no-use-before-define
    // eslint-disable-line no-use-before-define
   	多行禁用 no-use-before-define
    /* eslint-disable-line no-use-before-define */
    /* eslint-disable-line no-use-before-define */