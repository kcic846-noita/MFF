---
layout: page
title: Home
id: home
permalink: /
---

<div class="container">
  <!-- 왼쪽 메뉴 -->
  <nav class="sidebar">
    <ul>
      <li><a href="{{ site.baseurl }}/about">ABOUT</a></li>
      <li><a href="{{ site.baseurl }}/독서">독서</a></li>
      <li><a href="{{ site.baseurl }}/사진">사진</a></li>
      <li><a href="{{ site.baseurl }}/음악">음악</a></li>
      <li><a href="{{ site.baseurl }}/영상">영상</a></li>
    </ul>
  </nav>

  <!-- 오른쪽 메인 화면 -->
  <main class="content">
    <h1>Welcome! 🌱</h1>

    <p style="padding: 1.5em; background: #f5f7ff; border-radius: 4px;">
      Take a look at <span style="font-weight: bold">[[Your first note]]</span> to get started on your exploration.
    </p>

    <p>
      This digital garden template is free, open-source, and
      <a href="https://github.com/maximevaillancourt/digital-garden-jekyll-template">available on GitHub here</a>.
    </p>

    <p>
      The easiest way to get started is to read this
      <a href="https://maximevaillancourt.com/blog/setting-up-your-own-digital-garden-with-jekyll">step-by-step guide</a>.
    </p>

    <strong>Recently updated notes</strong>
    <ul>
      {% assign recent_notes = site.notes | sort: "last_modified_at_timestamp" | reverse %}
      {% for note in recent_notes limit: 5 %}
        <li>
          {{ note.last_modified_at | date: "%Y-%m-%d" }} —
          <a class="internal-link" href="{{ site.baseurl }}{{ note.url }}">{{ note.title }}</a>
        </li>
      {% endfor %}
    </ul>
  </main>
</div>

<style>
  .container {
    display: flex;
    max-width: 100%;
  }
  .sidebar {
    width: 180px;
    background: #f0f0f5;
    padding: 1em;
    height: 100vh; /* 세로 꽉 차게 */
    position: fixed; /* 스크롤 내려도 고정 */
    top: 0;
    left: 0;
  }
  .sidebar ul {
    list-style: none;
    padding-left: 0;
  }
  .sidebar li {
    margin: 1em 0;
  }
  .sidebar a {
    text-decoration: none;
    font-weight: bold;
    color: #333;
  }
  .sidebar a:hover {
    color: #0077cc;
  }
  .content {
    margin-left: 200px; /* 사이드바 공간만큼 비움 */
    padding: 2em;
    max-width: 46em;
  }
</style>