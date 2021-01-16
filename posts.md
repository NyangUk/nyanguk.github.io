---
layout: page
title: "Posts"
permalink: /posts/
main_nav: true
---

{% for category in site.categories %}
  {% capture cat %}{{ category | first }}{% endcapture %}
  <h2 id="{{cat}}">{{ cat | capitalize }}</h2>
  {% for desc in site.descriptions %}
    {% if desc.cat == cat %}
      <p class="desc"><em>{{ desc.desc }}</em></p>
    {% endif %}
  {% endfor %}
  <ul class="posts-list">
  {% for post in site.categories[cat] %}
    <li>
      <strong>
        <a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
      </strong>
      <span class="post-date">- {{ post.date | date_to_long_string }}</span>
    </li>
  {% endfor %}
  </ul>
  <script src="https://utteranc.es/client.js"
        repo="https://github.com/NyangUk/github-comments"
        issue-term="pathname"
        theme="github-dark-orange"
        crossorigin="anonymous"
        async>
  </script>
  {% if forloop.last == false %}<hr>{% endif %}
{% endfor %}
<br>
