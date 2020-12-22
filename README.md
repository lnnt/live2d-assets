# 为你的网站加入响应式的2D模型
##### 改自[EYHN/hexo-helper-live2d](https://github.com/EYHN/hexo-helper-live2d)
##### 预览：[Live 2D](https://huaji8.top/post/live2d-plugin-2.0)
![live-2d](https://github.com/stepbystep2/live2d-assets/raw/main/preview/live2d-plugin-2.0.jpg)
##### 国内仓库：[Gitee](https://gitee.com/xxxww/live2d-assets)
1. 在你的网站根目录下新建一个文件夹，命名为live2d  
2. 将你喜欢的模型所对应assets-*文件夹，及两个js文件放入你的live2d文件夹中  
3. 将assets-*文件夹重命名为assets  
4. 在你希望出现2D模型的页面的html代码中加入如下代码（注意更改代码中的模型名）：
```
<div>
    <canvas id="live2dcanvas" width="150" height="300"></canvas>
</div>
<style>
    #live2dcanvas {
        position: fixed;
        width: 150px;
        height: 300px;
        opacity: 0.7;
        right: 0px;
        z-index: 999;
        pointer-events: none;
        bottom: -20px;
    }
</style>
<script type="text/javascript" src="/live2d/device.min.js"></script>
<script type="text/javascript">
    const loadScript = function loadScript(c, b) {
        var a = document.createElement("script");
        a.type = "text/javascript";
        "undefined" != typeof b && (a.readyState ? a.onreadystatechange = function () {
            if ("loaded" == a.readyState || "complete" == a.readyState) a.onreadystatechange = null, b()
        } : a.onload = function () {
            b()
        });
        a.src = c;
        document.body.appendChild(a)
    };
    (function () {
        if ((typeof(device) != 'undefined') && (device.mobile())) {
            document.getElementById("live2dcanvas").style.width = '75px';
            document.getElementById("live2dcanvas").style.height = '150px';
        } else if (typeof(device) === 'undefined') console.error('Cannot find current-device script.');
        loadScript("/live2d/script.js", function () {
            loadlive2d("live2dcanvas", "/live2d/assets/模型名.model.json", 0.5);
        });
    })();
</script>  

```
