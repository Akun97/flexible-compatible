# flexible-compatible
flexible兼容PC版

源码地址（移动端兼容）：https://www.npmjs.com/package/lib-flexible

将flexible.js文件复制到项目里即可使用

配合px2rem-loader

```
npm install px2rem-loader -D
```

在main.js中

```
import '@/xxx/flexible'
```

配置webpack

若有使用scss、less等等，请将px2rem-loader放置在前面，因为加载顺序是从右到左，编译项目后会自动将样式大小转为rem单位

```
module: {
    rules: [
      {
        test: /\.scss$/,
        use: [
          'vue-style-loader',
          'css-loader', 
          {
            loader: 'px2rem-loader',
            options: {
              remUnit: 128,//设计稿宽度/10
              remPrecision: 8
            }
          },
          {
            loader: 'sass-loader',
            options: {
              outputStyle: 'expanded'//解决px2rem-loader注释失效
            }
          }
        ]
      }
    ]
  }
```

若不想转换成rem单位，样式添加/* no */

```
width: 100px;/*no*/
```

