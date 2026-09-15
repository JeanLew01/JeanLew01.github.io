---
layout: about
title: about
permalink: /
subtitle: Third-year Ph.D. Student · DSAI · Johns Hopkins University

profile:
  align: right
  image: false
  image_circular: false
  more_info:

selected_papers: true
social: true

announcements:
  enabled: false
  scrollable: true
  limit: 5

latest_posts:
  enabled: false
  scrollable: true
  limit: 3
---

<link rel="stylesheet" href="{{ '/assets/css/social-icons.css' | relative_url | bust_file_cache }}">

I'm a third-year Ph.D. student at the [Data Science and AI Institute (DSAI)](https://ai.jhu.edu/), [Johns Hopkins University](https://www.jhu.edu/), advised by [Prof. Enrique Mallada](https://mallada.ece.jhu.edu/). I have broad research interests in robotics, control, and verifiable autonomous systems. I am currently developing data-driven, learning-based, and generative methods for safety verification, particularly for complex systems where exact computation is intractable and guarantees must be obtained from limited data drawn from complex distributions. My research is generously supported in part by the [2026 JHU MINDS Fellowship](https://www.minds.jhu.edu/awards/minds-data-science-fellowships/).

I received my B.Sc. degree from the [School of Physics](https://phy.xjtu.edu.cn/English/Home.htm) at [Xi'an Jiaotong University](https://www.xjtu.edu.cn/), ranking 1st out of 95 students, and was honored as one of the Top-10 Undergraduate Students of the Year.

{% assign uploaded_cv = site.static_files | where: 'path', '/assets/pdf/cv.pdf' | first %}
{% assign cv_url = uploaded_cv.path | default: '/cv/' %}

More information can be found in my [CV]({{ cv_url | relative_url }}).
