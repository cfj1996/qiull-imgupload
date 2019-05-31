# qiull-imgupload

## Project setup
```
yarn install
```

### Compiles and hot-reloads for development
```
yarn run serve
```

### Compiles and minifies for production
```
yarn run build
```

### Run your tests
```
yarn run test
```

### Lints and fixes files
```
yarn run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

1.引入quill.js 文件,注意不能引入原始的quill.js
```
    import 'quill/dist/quill.core.css'
    import 'quill/dist/quill.snow.css'
    import 'quill/dist/quill.bubble.css'
    import $Quill from './plugins/quill'
```
2.配置options参数
```javascript
 options = {
        upload: '/api/igloo', // 文件上传地址
        headers: { // 自定义请求头
            'X-Custom-Header': 'foobar'
        },
        theme: 'snow',
        modules: { // 导航栏配置项
          toolbar: [
            ['bold', 'italic', 'underline', 'strike'],
            ['blockquote', 'code-block'],
            [{ 'header': 1 }, { 'header': 2 }],
            [{ 'list': 'ordered' }, { 'list': 'bullet' }],
            [{ 'script': 'sub' }, { 'script': 'super' }],
            [{ 'indent': '-1' }, { 'indent': '+1' }],
            [{ 'direction': 'rtl' }],
            [{ 'size': ['small', false, 'large', 'huge'] }],
            [{ 'header': [1, 2, 3, 4, 5, 6, false] }],
            [{ 'color': [] }, { 'background': [] }],
            [{ 'font': [] }],
            [{ 'align': [] }],
            ['clean'],
            ['link', 'image', 'video']
          ]
        },
      }
```

3. 设置代理

4.配置服务器

### 服务器端get请求接口返回值
```
 {
     code: 200
     msg: "quilljs"
 }
```

### 服务器端post请求接口返回值
```
 {
     code: 200
     url: "http://127.0.0.1:7001/public/uploads/fb3d66947fa94904e13a4a118a590ed5.png"
 }
```
