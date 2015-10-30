---
layout: page
title: R-sessions
tagline: MSc. Epi and PhD-CIH Programs - LMU München
---
{% include JB/setup %}

### Welcome to R-sessions WS15/16!
This is a webpage where you'll be able to find extra materials and interesting information about the R course WS15/16. This course is aimed at the MSc. Epidemiology and PhD-CIH students at the [LMU - München](http://www.uni-muenchen.de). You're welcome to browse the webpage and explore all the materials available so far!

### MSc. Epidemiology Webpage
All oficial materials concerning the R course will be uploaded to the [MSc. Epidemiology Webpage](http://www.en.msc-epidemiologie.med.uni-muenchen.de/msc/teaching/winterterm15_16/quantitative_methodes/index.html).

### Authors and Contributors
This webpage was coded and designed by [@darokun](https://github.com/darokun) using [GitHub Pages](https://pages.github.com/), [Jekyll](https://jekyllrb.com/), [Jekyll Bootstrap](http://jekyllbootstrap.com/) and [Jekyll Themes](http://jekyllthemes.org/). You're free to take a look at, modify, or use the code in this project.

    
## News
You may find all current information about these sessions here:


<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>


### Support or Contact
If you need anything, do not hesitate to write me an e-mail at <daloha.rodriguez@campus.lmu.de> or <daloharodriguez@gmail.com>.

