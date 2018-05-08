---
title: Markdown 拓展
---
# Markdown

[[toc]]

## 链接

### 内部链接

文件结构如下：

``` text
.
├─ README.md
├─ foo
│  ├─ README.md
│  ├─ one.md
│  └─ two.md
└─ bar
   ├─ README.md
   ├─ three.md
   └─ four.md
```

链接使用示例：

``` md
[Home](/) <!-- 跳转到根部的 README.md -->
[foo](/foo/) <!-- 跳转到 foo 文件夹的 index.html -->
[foo heading anchor](/foo/#heading) <!-- 跳转到 foo/index.html 的特定 anchor 位置 -->
[foo - one](/foo/one.html) <!-- 具体文件可以使用 .html 结尾 -->
[foo - two](/foo/two.md) <!-- 也可以用 .md -->
```

### 外部链接

外部链接自动设置 `target="_blank"`:

- [Vue](https://vuejs.org/)
- [VuePress](https://vuepress.vuejs.org/)
- [VuePress on GitHub](https://github.com/vuejs/vuepress)

## Front Matter

``` text
---
title: Blogging Like a Hacker
lang: en-US
meta:
  - name: description
    content: hello
  - name: keywords
    content: super duper SEO
---
```

## Github 风格的表格

Input

``` text
| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |
```

Output

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

## Emoji

Input

``` text
:tada: :100:
```

Output

:tada: :100:

## 目录

Input

``` md
[[toc]]
```

Output

[[toc]]

目录（Table of Contents）的渲染可以通过
[`markdown.toc`](https://vuepress.vuejs.org/zh/config/#markdowntoc)
选项来配置。

## 自定义容器

### 提示(Tip)

Input

``` md
::: tip
提示信息
:::
```

Output

::: tip
提示信息
:::

### 警告(Warning)

``` md
::: warning
警告信息
:::
```

Output

::: warning
警告信息
:::

### 错误(danger)

``` md
::: danger
错误信息
:::
```

Output

::: danger
错误信息
:::

### 自定义标题

Input

``` md
::: tip 标题
信息
:::
```

Output

::: tip 标题
信息
:::

## 代码高亮

Input

    ``` js
    export default {
    data () {
        return {
        msg: 'Highlighted!'
        }
    }
    }
    ```

Output

``` js
export default {
  data () {
    return {
      msg: 'Highlighted!'
    }
  }
}
```

## 进阶配置

VuePress 使用 [`markdown-it`](https://github.com/markdown-it/markdown-it) 来渲染 Markdown，上述大多数的拓展也都是通过自定义的插件实现的。想要进一步的话，你可以通过 `.vuepress/config.js` 的 `markdown` 选项，来对当前的 `markdown-it` 实例做一些自定义的配置：

``` js
module.exports = {
  markdown: {
    // markdown-it-anchor 的选项
    anchor: { permalink: false },
    // markdown-it-toc 的选项
    toc: { includeLevel: [1, 2] },
    config: md => {
      // 使用更多的 markdown-it 插件!
      md.use(require('markdown-it-xxx'))
    }
  }
}
```
