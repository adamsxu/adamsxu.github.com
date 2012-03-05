---
layout: default
title: Running
tagline: 
---
{% include JB/setup %}

<article class="unit-article layout-page">
  <div class="unit-inner unit-article-inner">
    <div class="content">      
      <div class="bd">
        <div class="entry-content">
          <ul class="posts">
            {% for post in site.posts limit:3 %}
              <div class="post">
                <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
                <div class="body">
                  {{ post.content }}
                </div>
                <div class="meta">
                  Posted on <a href="{{ post.url }}">{{ post.date | date_to_string }}</a>
                  </div>
              </div>
            {% endfor %}
          </ul>
        </div><!-- entry-content -->
      </div><!-- bd -->
    </div><!-- content -->
  </div><!-- unit-inner -->
</article>
