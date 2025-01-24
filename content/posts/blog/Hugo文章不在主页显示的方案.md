---
title: Hugo文章不在主页显示的方案
date: 2025-01-24T23:18:02+08:00
categories:
  - blog
tags:
  - blog
author: Delusion
description: A solution to prevent Hugo articles from appearing on the homepage.
slug: hugo-articles-dont-show
dir: blog
share: true
---

## 方案一

参考[# Hugo PaperMod 主题精装修](https://yunpengtai.top/posts/hugo-journey/#%e6%96%87%e7%ab%a0%e5%88%86%e7%b1%bb)

## 方案二

DeepSeek提供

根据你的需求，可以通过 Hugo 的 **分类（Taxonomy）** 和 **模板过滤** 功能实现：让某些文章不在主页展示，但可以通过分类页面（如 `分类/英语练习`）访问。以下是具体实现方法：

---
### 修改主页模板，排除特定分类

在 Hugo 的主页模板（通常是 `layouts/index.html` 或 `layouts/_default/home.html`）中，使用 `where` 函数过滤掉特定分类的文章：

```html
<!-- layouts/index.html -->
{{ define "main" }}
  <h1>最新技术文章</h1>
  {{ $filteredPages := where .Site.RegularPages "Params.categories" "not intersect" (slice "english-practice") }}
  {{ range $filteredPages }}
    <article>
      <h2><a href="{{ .RelPermalink }}">{{ .Title }}</a></h2>
      <p>{{ .Summary }}</p>
    </article>
  {{ end }}
{{ end }}
```

- **关键逻辑**：`not intersect` 表示排除包含 `english-practice` 分类的文章。
    
- 这会确保主页只展示非英语练习的文章。

### 添加分类导航链接（可选）

在导航栏或侧边栏中添加指向英语练习分类的链接，方便用户访问：

```html
<!-- layouts/partials/navbar.html -->
<a href="{{ "/categories/english-practice/" | relURL }}">英语作文练习</a>
```

### 最终效果

- **主页**：不再显示任何标记为 `english-practice` 的文章。
    
- **分类页**：访问 `/categories/english-practice/` 可看到所有英语练习文章。
    

## 方案一

参考[# Hugo PaperMod 主题精装修](https://yunpengtai.top/posts/hugo-journey/#%e6%96%87%e7%ab%a0%e5%88%86%e7%b1%bb)

## 方案二

DeepSeek提供

根据你的需求，可以通过 Hugo 的 **分类（Taxonomy）** 和 **模板过滤** 功能实现：让某些文章不在主页展示，但可以通过分类页面（如 `分类/英语练习`）访问。以下是具体实现方法：

---
### 修改主页模板，排除特定分类

在 Hugo 的主页模板（通常是 `layouts/index.html` 或 `layouts/_default/home.html`）中，使用 `where` 函数过滤掉特定分类的文章：

```html
<!-- layouts/index.html -->
{{ define "main" }}
  <h1>最新技术文章</h1>
  {{ $filteredPages := where .Site.RegularPages "Params.categories" "not intersect" (slice "english-practice") }}
  {{ range $filteredPages }}
    <article>
      <h2><a href="{{ .RelPermalink }}">{{ .Title }}</a></h2>
      <p>{{ .Summary }}</p>
    </article>
  {{ end }}
{{ end }}
```

- **关键逻辑**：`not intersect` 表示排除包含 `english-practice` 分类的文章。
    
- 这会确保主页只展示非英语练习的文章。

### 添加分类导航链接（可选）

在导航栏或侧边栏中添加指向英语练习分类的链接，方便用户访问：

```html
<!-- layouts/partials/navbar.html -->
<a href="{{ "/categories/english-practice/" | relURL }}">英语作文练习</a>
```

### 最终效果

- **主页**：不再显示任何标记为 `english-practice` 的文章。
    
- **分类页**：访问 `/categories/english-practice/` 可看到所有英语练习文章。
    
