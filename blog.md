---
layout: page
title: 文章列表
permalink: /blog/
---

<div class="blog-list">
  <div class="blog-filters">
    <a href="{{ '/blog/' | relative_url }}" class="filter-tag filter-all">全部</a>
    <a href="{{ '/blog/?category=learning' | relative_url }}" class="filter-tag">📖 学习笔记</a>
    <a href="{{ '/blog/?category=project' | relative_url }}" class="filter-tag">🚀 项目复盘</a>
    <a href="{{ '/blog/?category=debug' | relative_url }}" class="filter-tag">🐛 踩坑记录</a>
    <a href="{{ '/blog/?category=tech' | relative_url }}" class="filter-tag">💡 技术分享</a>
    <a href="{{ '/blog/?category=reading' | relative_url }}" class="filter-tag">📚 读书笔记</a>
  </div>

  <div class="post-grid">
    {% for post in site.posts %}
      {% include post-card.html post=post %}
    {% endfor %}
  </div>

  {% if site.posts.size == 0 %}
  <div class="empty-state">
    <p>还没有文章，敬请期待...</p>
  </div>
  {% endif %}
</div>
