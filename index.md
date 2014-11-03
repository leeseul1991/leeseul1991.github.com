---
layout: page
---
{% include JB/setup %}
<font color="red"><b>---------------------------------------------------------------------------------------------------------------------------------------------------</b></font>

<img src="http://cfile23.uf.tistory.com/image/172A0B3950641DAB264C91" width = "820" height = "280">

<font color="red"><b>---------------------------------------------------------------------------------------------------------------------------------------------------</b></font>
<div>
<br></br>
<h1>&nbsp&nbsp공대녀's 학습블로그 </h1>
<br></br>
<h2>&nbsp&nbsp&nbsp안녕하세요? 공대녀 입니다.</h2>
<h2>&nbsp&nbsp&nbsp우리함께 열심히 <font color="red"><b>C언어</b></font>를 공부해보아요.</h2>
<br></br>
<h3>&nbsp&nbsp&nbsp교수님 사랑합니다<font color="red">♥</font></h3>
<br></br>
</div>


<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

## Contact

      name : 공대녀
      email : an_dms@naver.com
      github : leeseul1991.github.com


