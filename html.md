# html 图片转base64
```html
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABgAAAAYCAMAAADXqc3KAAAAMFBMVEVMaXHYHQXYHQXYHQXYHQXYHQXYHQXYHQXYHQXYHQXYHQXYHQXXHQXYHQXXHQXYHQWhiOGSAAAAD3RSTlMAAvsbC9zQjuMq8H+oPL4V+AdoAAAACXBIWXMAAAsTAAALEwEAmpwYAAAArUlEQVQokX1SCQ7EIAhEELza8P/fbvBa1m5KYmmZziiDAK8R5iPsj1UORNFeI9HCLcUmtXIiSlyrtLiYhbVHziNzGUhkRVS/2GQDJMXxJ66syShG0J/AQaGjbIEEAOUEcAIx/5cKcD2BC4K1cUipam/EnXcR+mmtFfEIqmyvyO2PyvR1sWwENe9650w1VHH17vw1vLqm525WzRjND3Aht8j9qA+5Q8aP/v3O9PgAjUUNrh6rCM4AAAAASUVORK5CYII="/>
```


>调用iconfont
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=, initial-scale=1.0">
    <title>Document</title>

    <style>
        html {
            font-family: iconfont;
          
        }

        /* 在线链接服务仅供平台体验和调试使用，平台不承诺服务的稳定性，企业客户需下载字体包自行发布使用并做好备份。 */
        @font-face {
            font-family: 'iconfont';
            /* Project id 4353622 */
            src: url('//at.alicdn.com/t/c/font_4353622_5vpqb0goywo.woff2?t=1701347316648') format('woff2'),
                url('//at.alicdn.com/t/c/font_4353622_5vpqb0goywo.woff?t=1701347316648') format('woff'),
                url('//at.alicdn.com/t/c/font_4353622_5vpqb0goywo.ttf?t=1701347316648') format('truetype');
        }
    </style>
</head>

<body>

    <span class="iconfont">&#xe61e</span>

</body>

</html>
```