---
layout: page
title: Sản phẩm
icon: fas fa-cubes
order: 5
---

## 🚀 Sản phẩm tự build

Trang này tự động gom các bài viết sản phẩm từ `_posts`.

## 📚 Bài viết theo sản phẩm

{% assign product_posts = "" | split: "" %}
{% for post in site.posts %}
  {% assign is_product = false %}

  {% if post.categories contains "Product" or post.categories contains "SanPham" or post.categories contains "San-Pham" or post.categories contains "Sản phẩm" %}
    {% assign is_product = true %}
  {% endif %}

  {% if post.tags contains "product" or post.tags contains "san-pham" or post.tags contains "portfolio" or post.tags contains "case-study" %}
    {% assign is_product = true %}
  {% endif %}

  {% if is_product %}
    {% assign product_posts = product_posts | push: post %}
  {% endif %}
{% endfor %}

{% if product_posts.size > 0 %}
{% for post in product_posts %}
### [{{ post.title }}]({{ post.url | relative_url }})

{{ post.excerpt | strip_html | truncate: 220 }}

- Ngày đăng: `{{ post.date | date: "%d-%m-%Y" }}`
<!-- - Danh mục: `{{ post.categories | join: ", " }}` -->
<!-- - Tags: `{{ post.tags | join: ", " }}` -->


{% endfor %}
{% else %}
Chưa có bài viết sản phẩm nào.

Để bài viết xuất hiện ở tab này, thêm một trong các metadata sau vào front matter của post:

```yaml
categories: [Product]
```

hoặc:

```yaml
tags: [product]
```
{% endif %}
