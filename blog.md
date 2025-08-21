---
layout: page
title: Blog
description: All my blog posts in one place.
permalink: /blog/
---

## All Posts

{% if site.posts.size > 0 %}
    <div class="posts-list">
        {% for post in site.posts %}
            <article class="post-card">
                <header class="post-card-header">
                    <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
                    <div class="post-card-meta">
                        <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %d, %Y" }}</time>
                        {% if post.categories.size > 0 %}
                            • <span class="category">{{ post.categories.first }}</span>
                        {% endif %}
                    </div>
                </header>
                <div class="post-card-content">
                    <p>{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
                </div>
                <footer class="post-card-footer">
                    <a href="{{ post.url | relative_url }}" class="read-more">Read More →</a>
                </footer>
            </article>
        {% endfor %}
    </div>
{% else %}
    <div class="no-posts">
        <h3>No posts yet!</h3>
        <p>I'm working on creating some great content. Check back soon for new posts!</p>
        <a href="/about/" class="btn btn-outline">Learn More About Me</a>
    </div>
{% endif %}

## Categories

{% assign categories = site.categories | sort %}
{% if categories.size > 0 %}
    <div class="categories-list">
        {% for category in categories %}
            <a href="/categories/{{ category[0] | slugify }}" class="category-tag">
                {{ category[0] }} ({{ category[1].size }})
            </a>
        {% endfor %}
    </div>
{% endif %}