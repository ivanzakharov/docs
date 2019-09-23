---
layout: home
title: Architecting Microsoft Dynamics 365 for Finance and Operations
description: "This is an open source project that helps Microsoft Dynamics 365 for Finance and Operations developers improve their skills and approaches to build the best solutions. Developers can find information that describes the rules of development approach and recommended patterns for developing customizations for Microsoft Dynamics 365 for Finance and Operations.
Instructions include an overview of the architectural and development features and the tools available in the development environment. It is also covers the essentials of doing development in Microsoft Dynamics 365 for Operations, including creating tables, classes, forms, and reports, using models, Visual Studio and other fun features.
Every Microsoft Dynamics 365 for Finance and Operations developer can contribute with this open-source project. Please join us!"
group: what-s-new
redirect_from:
  - "/what-s-new/"
toc: true
---

<div class="posts">
  {% for post in site.posts %}
    <article class="post mb-3">

      <h1><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h1>
      <div class="entry">
        {{ post.excerpt }}
      </div>
	    <a href="{{ site.baseurl }}{{ post.url }}" class="read-more">Read More</a>
    </article>
  {% endfor %}
</div>