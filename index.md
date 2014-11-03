---
layout: page
---
{% include JB/setup %}

<img src="http://cfile23.uf.tistory.com/image/172A0B3950641DAB264C91" width = "900" height = "280">


<div>
<br></br>
<h1>      공대녀's 학습블로그 </h1>
<br></br>
<br></br>
<h2>      안녕하세요? 공대녀 입니다.</h2>
<br></br>
<h2>      우리함께 열심히 C언어를 공부해보아요.</h2>
<br></br>
<h3>      교수님 사랑합니다♥</h3>
<br></br>
<br></br>
</div>


      name : 공대녀
      email : an_dms@naver.com
      github : leeseul1991.github.com


<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

## To-Do

This theme is still unfinished. If you'd like to be added as a contributor, [please fork](http://github.com/plusjade/jekyll-bootstrap)!
We need to clean up the themes, make theme usage guides with theme-specific markup examples.


