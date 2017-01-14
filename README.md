# 微信小程序 wepyjs 第三方图片懒加载组件

## 说明
[wxapp-img-loader](https://github.com/o2team/wxapp-img-loader)只能用于小程序原生开发，因此需要一个适用于[wepy](https://github.com/wepyjs/wepy)使用的组件。

## 使用

### 安装组件
```
npm install wepy-img-loader --save
```

### 引入组件
``` javascript
// index.wpy
<template>
    <imgloader />
</template>
<script>
    import wepy from 'wepy';
    import ImgLoader from 'wepy-img-loader';

    export default class Index extends wepy.page {
        components = {
            imgloader: ImgLoader
        }
    }
</script>
```

### 调用方法
``` javascript
//缩略图 80x50 3KB
const imgUrlThumbnail = 'http://storage.360buyimg.com/mtd/home/lion1483683731203.jpg'
//原图 3200x2000 1.6MB
const imgUrlOriginal = 'http://storage.360buyimg.com/mtd/home/lion1483624894660.jpg'

this.msg = '大图正在拼命加载...'
this.imgUrl = imgUrlThumbnail

this.$invoke('imgloader', 'load', imgUrlOriginal, (err, data) => {
    this.msg = '大图加载完成~'
    if (!err) {
    this.imgUrl = data.src
    }
    this.$apply()
})
```

## Thanks
### [wepy](https://github.com/wepyjs/wepy)
### [wxapp-img-loader](https://github.com/o2team/wxapp-img-loader)