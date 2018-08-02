---
layout: page
permalink: /cli/
title: CLI Snippets
---

<div id="archives">
This page contains snippets of code explaining usage for various tools.
{% for article in site.cli %}
  <div class="archive-group">
    {% capture cli_name %}{{ cli | upcase }}{% endcapture %}
    <div id="#{{ cli_name | slugize }}"></div>
    <p></p>

    <h4><a href="{{ site.baseurl }}{{ article.url }}">{{article.title}}</a></h4>
  </div>
{% endfor %}
</div>
