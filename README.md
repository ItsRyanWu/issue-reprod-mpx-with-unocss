# issue-reprod-mpx-with-unocss

> A mpx project

## 复现步骤：
1. 安装 unocss 与 @unocss/webpack
``` sh
npm i unocss @unocss/webpack -D
```

2. 使用 @unocss/webpack 插件
``` javascript
//getPlugins.js line 94
plugins.push(UnoCSS())
```

3. 配置 unocss

在项目根目录中新建 `unocss.config.ts`

4. 引入 unocss 产物
```html
// app.mpx
<style src="uno.css"></style>
```

5. 在项目中使用 unocss 样式
```html
// index.mpx
<template>
  <list class="bg-red h-[50vh]"></list>
</template>
```

6. 运行项目
```sh
npm run watch
```

7. 观察 unocss 样式是否注入 wxss
   
结果发现生成的样式并未注入 wxss, 而是将样式作为字符串生成在了 `dist/wx/app.js` line 122，结果不正常，没有达到预期效果。

