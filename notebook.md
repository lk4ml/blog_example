---
layout: page
permalink: /notebook/
title: Notebook
---

<div id="archives">
Daily notebook for stuff that I can't or won't write a proper article about. :man_shrugging:

{% for article in site.notebook %}
  <div class="archive-group">
    {% capture notebook_name %}{{ notebook | upcase }}{% endcapture %}
    <div id="#{{ notebook_name | slugize }}"></div>
    <p></p>

    <h4><a href="{{ site.baseurl }}{{ article.url }}">{{article.title}}</a></h4>
  </div>
{% endfor %}
</div>
