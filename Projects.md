---
layout: projects
title: Projects
subtitle: "Academic Works & Competition Essays"
---

<div class="posts-list">
  {% for post in site.posts %}
    {% if post.categories contains "modeling" %}
      <article class="post-preview" style="margin-bottom: 20px;">
        
        <!-- 标题 -->
        <h2 class="post-title" style="margin-bottom: 5px; font-size: 1.75rem;">
          <a href="{{ post.url | relative_url }}" style="text-decoration: none; color: var(--text-col);">{{ post.title }}</a>
        </h2>
        
        <!-- 副标题 -->
        {% if post.subtitle %}
          <h3 class="post-subtitle" style="margin: 0 0 10px 0; color: #666; font-weight: normal; font-size: 1.25rem;">
            {{ post.subtitle }}
          </h3>
        {% endif %}
        
        <!-- 日期和作者并列 -->
        <p class="post-meta" style="font-size: 0.9rem; color: #888; margin: 10px 0; font-style: italic;">
          {% if post.author %}
            By {{ post.author }} · 
          {% endif %}
          Posted on {{ post.date | date: "%B %d, %Y" }}
        </p>
        
        <!-- 简介（21字截断）+ 缩略图并列 -->
        <div style="display: flex; align-items: flex-start; gap: 20px; flex-wrap: wrap;">
          
          <!-- 左侧：简介 -->
          <div style="flex: 1; min-width: 250px;">
            <div class="post-entry" style="color: #444; line-height: 1.6;">
              {{ post.content | strip_html | truncate: 126 }}
              {% assign excerpt_length = 21 %}
              {% assign excerpt_word_count = post.content | strip_html | size %}
              {% if excerpt_word_count > excerpt_length %}
                <a href="{{ post.url | relative_url }}" class="post-read-more" style="font-weight: 600; color: var(--link-col);">[Read&nbsp;More]</a>
              {% endif %}
            </div>
          </div>
          
          <!-- 右侧：缩略图 -->
          {% if post.thumbnail-img %}
            <div class="post-image" style="flex-shrink: 0; margin-left: 10px;">
              <a href="{{ post.url | relative_url }}" aria-label="Thumbnail">
                <img src="{{ post.thumbnail-img | relative_url }}" 
                     alt="Post thumbnail" 
                     style="width: 12rem; height: 12rem; object-fit: cover; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.1);">
              </a>
            </div>
          {% endif %}
          
        </div>
        
        <!-- 标签（在简介下方） -->
        {% if post.tags.size > 0 %}
          <div class="blog-tags" style="margin-top: 15px;">
            <span style="font-weight: 600;">Tags:</span>
            {% for tag in post.tags %}
              <a href="{{ '/tags' | relative_url }}#{{- tag -}}" 
                 style="display: inline-block; background: #f0f0f0; padding: 2px 8px; border-radius: 12px; font-size: 0.8rem; margin-left: 5px; color: #555; text-decoration: none;">
                {{- tag -}}
              </a>
            {% endfor %}
          </div>
        {% endif %}
        
        <hr style="margin: 15px 0; border: none; border-top: 1px solid #eee;">
      </article>
    {% endif %}
  {% endfor %}
</div>