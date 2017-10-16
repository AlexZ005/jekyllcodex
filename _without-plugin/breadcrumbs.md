---
title: Breadcrumbs
---

### Introduction

...

### How it works

```
{% raw %}{% assign crumbs = page.url | remove:'/index.html' | split: '/' %}
<a href="/">Home</a>
{% for crumb in crumbs offset: 1 %}
  {% if forloop.last %}
    / {{ crumb | replace:'-',' ' | remove:'.html' | capitalize }}
  {% else %}
    / <a href="{% assign crumb_limit = forloop.index | plus: 1 %}{% for crumb in crumbs limit: crumb_limit %}{{ crumb | append: '/' }}{% endfor %}">{{ crumb | replace:'-',' ' | remove:'.html' | capitalize }}</a>
  {% endif %}
{% endfor %}{% endraw %}
```

### Installation

Step 1. Download the file [breadcrumbs.html]()
Step 2. Save the file in the ‘_includes’ directory of your project
Step 3. Add the following line to your layout on the place where you want the breadcrumbs to appear:

```
{% raw %}{% include breadcrumbs.html %}{% endraw %}
```