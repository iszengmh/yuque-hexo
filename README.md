# yuque-hexo

[![NPM version][npm-image]][npm-url]
[![build status][travis-image]][travis-url]
[![Test coverage][codecov-image]][codecov-url]
[![David deps][david-image]][david-url]
[![Known Vulnerabilities][snyk-image]][snyk-url]
[![npm download][download-image]][download-url]

[npm-image]: https://img.shields.io/npm/v/yuque-hexo.svg?style=flat-square
[npm-url]: https://npmjs.org/package/yuque-hexo
[travis-image]: https://img.shields.io/travis/x-cold/yuque-hexo.svg?style=flat-square
[travis-url]: https://travis-ci.org/x-cold/yuque-hexo
[codecov-image]: https://codecov.io/gh/x-cold/yuque-hexo/branch/master/graph/badge.svg
[codecov-url]: https://codecov.io/gh/x-cold/yuque-hexo
[david-image]: https://img.shields.io/david/x-cold/yuque-hexo.svg?style=flat-square
[david-url]: https://david-dm.org/x-cold/yuque-hexo
[snyk-image]: https://snyk.io/test/npm/yuque-hexo/badge.svg?style=flat-square
[snyk-url]: https://snyk.io/test/npm/yuque-hexo
[download-image]: https://img.shields.io/npm/dm/yuque-hexo.svg?style=flat-square
[download-url]: https://npmjs.org/package/yuque-hexo

A downloader for articles from yuque

# Usage

## Premise

事先拥有一个 [hexo](https://github.com/hexojs/hexo) 项目，在`package.json`配置相关信息，详见 [例子](#Example)。

## Config

> package.json

```json
{
  "name": "your hexo project",
  "yuqueConfig": {
    "baseUrl": "https://www.yuque.com/api/v2",
    "login": "yinzhi",
    "repo": "blog",
    "mdNameFormat": "title",
    "postPath": "source/_posts/yuque"
  }
}
```

"mdNameFormat": 生成的 Markdown 文件的文件名，可以选择 "title" 或者 "slug"，默认 "title"，slug 是语雀的永久链接名，一般是几个随机字母。

"postPath": 存放从语雀下载的 Markdown 文件的文件夹，除了 Hexo ，理论上可以支持其他支持 Front-matter 的 Markdown 静态博客

## Install

```
npm i -g yuque-hexo
# or
npm i --save-dev yuque-hexo
```

## Sync

```
yuque-hexo sync
```

## Clean

```
yuque-hexo clean
```

## Npm Scripts

```json
{
  "dev": "npm run sync && hexo s",
  "sync": "yuque-hexo sync",
  "clean:yuque": "yuque-hexo clean"
}
```

## Debug

```
DEBUG=yuque-hexo.* yuque-hexo sync
```

# Notice

1. 语雀同步过来的文章会生成两部分文件；

    - yuque.json: 从语雀 API 拉取的数据
    - source/_posts/yuque/*.md: 生成的 md 文件

2. 支持配置front-matter, 语雀编辑器编写示例如下:
    - 语雀编辑器示例，可参考[原文](https://www.yuque.com/u46795/blog/dlloc7)：
    ![image.png](https://cdn.nlark.com/yuque/0/2019/png/155457/1547033073596-797e3d68-fac4-40fd-8e8d-16ea1da4b705.png)
    语雀编辑器转换成的markdown 如下（已做兼容）：
    ```markdown
      tags: [hexo, node]<br />date: 2018-06-09<br />categories: 前端

      ---
    ```

    - 标准 markdown 示例：

    ```markdown
      date: 2015-04-18 00:00:00
      tags: [css]
      categories: CSS 
      ---
    ```

    > 注意：分割线不能少，兼容一个或多个属性的自定义

# Example

https://github.com/x-cold/blog/blob/master/package.json

# Changelog

### v1.1.1

- 支持 hexo-front-matter，可以在文章中编辑 tags / date 等属性

### v1.2.1

- 修复 windows 环境下命令行报错的问题
- 支持自定义文件夹和博客文件命名

### v1.3.1

- 修复 front-matter 处理格式问题
