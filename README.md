#  gitbook制作mobi书籍
[官方文档](https://toolchain.gitbook.com/config.html)
[kindle图书制作说明](https://bookfere.com/post/287.html)
```
.
├── book.json
├── README.md
├── SUMMARY.md
├── chapter-1/
|   ├── README.md
|   └── something.md
└── chapter-2/
├── README.md
└── something.md
```
### 封面
封面用于所有电子书格式。您可以自己提供一个，也可以使用 [autocover plugin](https://plugins.gitbook.com/plugin/autocover) 生成一个。
要提供封面，请将 **cover.jpg** 文件放在书本的根目录下。添加一个 **cover_small.jpg** 将指定一个较小版本的封面。封面应为 JPEG 文件。
好的封面应该遵守以下准则：
* cover.jpg 的尺寸为 1800x2360 像素，cover_small.jpg 为 200x262
* 没有边界
* 清晰可见的书名
* 任何重要的文字应该在小版本中可见
### 个性化配置
在Kindle中浏览mobi格式文件完整的书名，封面等。

```
{
    "title": "<#书名#>",
    "author": "<#作者#>",
    "description": "<#简介#>",
    "language": "zh-hans",
    "gitbook": "<#出版号#>",
    "styles": {
        "website": "./styles/website.css"
    },
    "structure": {
        "readme": "README.md"
    },
    "links": {
        "sidebar": {
            "我的狗窝": "https://blankj.com"
        }
    },
    "plugins": [
        "-sharing",
        "splitter",
        "expandable-chapters-small",
        "anchors",

        "github",
        "github-buttons",
        "donate",
        "sharing-plus",
        "anchor-navigation-ex",
        "favicon"
    ],
    "pluginsConfig": {
        "github": {
            "url": "https://github.com/huos3203"
        },
    "github-buttons": {
        "buttons": [{
            "user": "huos3203",
            "repo": "<#库名#>",
            "type": "star",
            "size": "small",
            "count": true
        }
        ]
    },
    "donate": {
        "alipay": "./source/images/donate.png",
        "title": "",
        "button": "赞赏",
        "alipayText": " "
    },
    "sharing": {
        "douban": false,
        "facebook": false,
        "google": false,
        "hatenaBookmark": false,
        "instapaper": false,
        "line": false,
        "linkedin": false,
        "messenger": false,
        "pocket": false,
        "qq": false,
        "qzone": false,
        "stumbleupon": false,
        "twitter": false,
        "viber": false,
        "vk": false,
        "weibo": false,
        "whatsapp": false,
        "all": [
            "google", "facebook", "weibo", "twitter",
            "qq", "qzone", "linkedin", "pocket"
        ]
    },
    "anchor-navigation-ex": {
        "showLevel": false
    },
    "favicon":{
        "shortcut": "./source/images/favicon.jpg",
        "bookmark": "./source/images/favicon.jpg",
        "appleTouch": "./source/images/apple-touch-icon.jpg",
        "appleTouchMore": {
            "120x120": "./source/images/apple-touch-icon.jpg",
            "180x180": "./source/images/apple-touch-icon.jpg"
        }
    }
    }
}
```

### 发布书籍
1. 创建 gh-pages 分支
执行如下命令来创建分支，并且删除不需要的文件：
```
$ git checkout --orphan gh-pages
$ git rm --cached -r .
$ git clean -df
$ rm -rf *~
```
2. 添加静态网页到分支库中
现在，目录下应该只剩下 _book 目录了，首先，忽略一些文件：
```
$ echo "*~" > .gitignore
$ echo "_book" >> .gitignore
$ git add .gitignore
$ git commit -m "Ignore some files"
```
然后，加入 _book 下的内容到分支中：
```
$ cp -r _book/* .
$ git add .
$ git commit -m "Publish book"
$ git push -u origin gh-pages #
```

[参考](http://www.chengweiyang.cn/gitbook/github-pages/README.html)
