---
layout: projects
title: Projects
subtitle: "Academic Works & Competition Essays"
---

<div class="posts-list">
  {% for post in site.posts %}
    {% if post.categories contains "modeling" %}
      <article class="post-preview" style="margin-bottom: 40px;">
        <div style="display: flex; align-items: flex-start; gap: 20px; flex-wrap: wrap;">
          
          <!-- 左侧文本 -->
          <div style="flex: 1; min-width: 250px;">
            <h3 style="margin-bottom: 8px;">
              <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
            </h3>
            {% if post.subtitle %}
              <h4 style="margin: 5px 0; color: #666; font-weight: normal;">{{ post.subtitle }}</h4>
            {% endif %}
            <div style="font-size: 0.85em; color: #888; margin: 10px 0;">
              {% if post.author %}{{ post.author }} · {% endif %}
              {{ post.date | date: "%Y年%m月%d日" }}
            </div>
            
            <!-- 关键修改：truncate 21 字符 -->
            <div style="margin-top: 12px; color: #444;">
              {{ post.content | strip_html | truncate: 21 }}...
            </div>
          </div>
          
          <!-- 右侧缩略图 -->
          {% if post.thumbnail-img %}
            <div style="flex-shrink: 0;">
              <a href="{{ post.url | relative_url }}">
                <img src="{{ post.thumbnail-img | relative_url }}" 
                     alt="论文配图" 
                     style="width: 150px; border-radius: 8px;">
              </a>
            </div>
          {% endif %}
          
        </div>
        <hr style="margin: 30px 0; border-top: 1px solid #eee;">
      </article>
    {% endif %}
  {% endfor %}
</div>