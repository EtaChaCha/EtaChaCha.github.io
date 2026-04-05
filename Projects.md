---
layout: home
title: Projects
subtitle: "Academic Works & Competition Essays"
---

<div class="posts-list">
  {% for post in site.posts %}
    {% if post.categories contains "modeling" %}
      <article class="post-preview">
        <div style="display: flex; align-items: flex-start; gap: 20px; flex-wrap: wrap; margin-bottom: 30px;">
          <!-- 左侧：文本信息 -->
          <div style="flex: 1;">
            <h3 style="margin-bottom: 5px;">
              <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
            </h3>
            {% if post.subtitle %}
              <h4 style="margin-top: 0; color: #666; font-weight: normal;">{{ post.subtitle }}</h4>
            {% endif %}
            <div class="post-meta" style="font-size: 0.9em; color: #888; margin: 8px 0;">
              {% if post.author %}{{ post.author }} · {% endif %}
              {{ post.date | date: "%Y年%m月%d日" }}
            </div>
            {% if post.tags %}
              <div class="post-tags" style="margin: 8px 0;">
                {% for tag in post.tags %}
                  <span class="tag" style="background: #f0f0f0; padding: 2px 8px; border-radius: 15px; font-size: 0.75rem; margin-right: 5px;">{{ tag }}</span>
                {% endfor %}
              </div>
            {% endif %}
            <!-- 摘要：自动截取正文前21个字符，并添加 Read More 链接 -->
            <div class="post-excerpt" style="margin-top: 8px;">
              {{ post.content | strip_html | truncate: 21, "" }}
              {% assign stripped_content = post.content | strip_html %}
              {% if stripped_content.size > 21 %}
                <a href="{{ post.url | relative_url }}" style="margin-left: 5px;">[Read More]</a>
              {% endif %}
            </div>
          </div>
          <!-- 右侧：缩略图 -->
          {% if post.thumbnail-img %}
            <div style="flex-shrink: 0;">
              <img src="{{ post.thumbnail-img | relative_url }}" alt="论文配图" style="width: 120px; height: auto; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.1);">
            </div>
          {% endif %}
        </div>
        <hr style="margin: 20px 0;">
      </article>
    {% endif %}
  {% endfor %}
</div>