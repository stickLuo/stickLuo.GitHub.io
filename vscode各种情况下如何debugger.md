1、在debugger for chrome插件中
分为两种形式：
  1、node项目等，如vue-cli
      自带nodejs（可能有自带有插件）
  2、纯html等文件
      直接按设置图标进行配置，打开如下，可以匹配多个browser-preview是内嵌的浏览器，chrome外置的谷歌，可以通过url精确拦截
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations":[ 
    { 
        "type": "browser-preview",
        "request": "attach",
        "name": "内嵌插件调试",
        "webRoot": "${workspaceRoot}"
    },
    {
        "type": "chrome",
        "request": "launch",
        "name": "Launch Chrome against localhost",
        "url": "http://localhost:8080",
        "webRoot": "${workspaceFolder}"
    }
    ]
}
![image](https://user-images.githubusercontent.com/49802891/140650353-4e36e250-27a0-47c3-9412-653aec3de0db.png)
 1.1、可以看到  require有两种:attach和launch  前者是 不跑 但是我拦截 并debugger  后者是提供项目并且debugger
      前提：
          插件1：browser-preview
          插件2：live server
          插件3：open in brower
      解释：
          插件2和3的区别是：插件3 相当于通过浏览器直接打开本地的html页面，缺点是更改内容后无法自动更新，需要刷新页面
                           插件2  相当于在简单的项目中加载了某个页面，个人理解就是一个简单的程序，可以动态更新
          插件1的作用是内嵌浏览器                
      结论：
          针对于正常的项目launch
          针对于live server这种的需要使用attach
      
