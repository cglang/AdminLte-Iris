# 这是个什么东西

不想整一些花里胡哨的东西，就找到了 [AdminLTE](https://github.com/ColorlibHQ/AdminLTE) 这个前端快速开发框架，下载下来发下他的侧边栏做的不是很喜欢，我以我就自行修改了一下，并对页面的加载稍微做了一点处理。

## 侧边栏

侧边栏的加载是通过一组数据，这组数据可以自己写死在前端，也可以通过后端动态生成，理论上是支持无限深度的侧边栏，数据结构如下。分组的话值支持第一级进行分组，再往下就不再支持了，所以只在第一级进行了 `group` 的定义，另外在往更深的层次之中，用于展开的那个标签是不用写 `url` 属性的，这里我多提一句吧，其实写了也没关系，因为根本用不到。

```json
[
  {
    "group": "分组1",
    "items": [
      {
        "name": "测试1",
        "url": "/pages/test/index.html",
        "ico": "fa-cubes"
      }
    ]
  },
  {
    "group": "分组2",
    "items": [
      {
        "name": "Dashboard1",
        "url": "/pages/dashboard/index.html",
        "ico": "fa-bell-slash"
      },
      {
        "name": "分组2-1",
        "ico": "fa-heartbeat",
        "items": [
          {
            "name": "Dashboard1",
            "url": "/pages/dashboard/index.html",
            "ico": "fa-bell-slash"
          },
          {
            "name": "Dashboard2",
            "url": "/pages/dashboard/index.html",
            "ico": "fa-heartbeat"
          }
        ]
      }
    ]
  }
]
```

## 页面的加载

页面的加载我没有使用 `iframe`，这里我使用请求一个页面然后动态加载到指定的便签内，这里我使用了`JQuery`，当然因为 AdminLTE 默认用了`JQuery`所以我顺便就是用它，不喜欢的话可以自行更换。

```js
$.get("./pages/dashboard/index.html", (html) => {
  $("#app").html(html);
});
```

## 其他

界面的布局及样式我只保留了我喜欢的风格，不喜欢的话就得自行修改了，样式方面只对 AdminLTE 做了删除，没有添加任何的新的，界面的话都被我删干净了，只留了一个测试页面，用来自己写写小玩具还是很好用的，轻量的很。