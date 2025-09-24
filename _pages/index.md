---
layout: page
title: Home
id: home
permalink: /
---

<div class="main-container">
  <!-- 세로 메뉴 -->
  <nav class="sidebar-nav">
    <ul class="nav-menu">
      <li><a href="#about" class="nav-link active" data-section="about">ABOUT</a></li>
      <li><a href="#reading" class="nav-link" data-section="reading">독서</a></li>
      <li><a href="#photos" class="nav-link" data-section="photos">사진</a></li>
      <li><a href="#music" class="nav-link" data-section="music">음악</a></li>
      <li><a href="#videos" class="nav-link" data-section="videos">영상</a></li>
    </ul>
  </nav>

  <!-- 콘텐츠 영역 -->
  <main class="content-area">
    <!-- ABOUT 섹션 -->
    <section id="about" class="content-section active">
      <h1>Welcome to My Digital Garden! 🌱</h1>
      <p class="intro-text">
        이곳은 제가 생각하고 배우고 경험한 것들을 기록하는 디지털 정원입니다.
        좌측 메뉴를 통해 다양한 콘텐츠를 둘러보세요.
      </p>
      
      <div class="recent-updates">
        <h3>최근 업데이트</h3>
        <ul>
          {% assign recent_notes = site.notes | sort: "last_modified_at_timestamp" | reverse %}
          {% for note in recent_notes limit: 5 %}
            <li>
              {{ note.last_modified_at | date: "%Y-%m-%d" }} — <a class="internal-link" href="{{ site.baseurl }}{{ note.url }}">{{ note.title }}</a>
            </li>
          {% endfor %}
        </ul>
      </div>
    </section>

    <!-- 독서 섹션 -->
    <section id="reading" class="content-section">
      <h1>📚 독서</h1>
      <p>읽었던 책들과 독서 노트를 모아둔 공간입니다.</p>
      
      <div class="books-grid">
        {% assign reading_notes = site.notes | where_exp: "note", "note.path contains '/reading/'" | sort: "date" | reverse %}
        {% if reading_notes.size > 0 %}
          {% for note in reading_notes %}
            <div class="book-card">
              <h3><a class="internal-link" href="{{ site.baseurl }}{{ note.url }}">{{ note.title }}</a></h3>
              {% if note.author %}
                <p class="book-author">저자: {{ note.author }}</p>
              {% endif %}
              {% if note.excerpt %}
                <p class="book-excerpt">{{ note.excerpt | strip_html | truncatewords: 20 }}</p>
              {% endif %}
              <small class="book-date">{{ note.date | date: "%Y-%m-%d" }}</small>
            </div>
          {% endfor %}
        {% else %}
          <p class="empty-state">아직 독서 노트가 없습니다. 첫 번째 책 리뷰를 작성해보세요!</p>
        {% endif %}
      </div>
    </section>

    <!-- 사진 섹션 -->
    <section id="photos" class="content-section">
      <h1>📷 사진</h1>
      <p>여행과 일상의 순간들을 담은 사진들입니다.</p>
      
      <div class="photos-grid">
        {% assign photo_notes = site.notes | where_exp: "note", "note.path contains '/photos/'" | sort: "date" | reverse %}
        {% if photo_notes.size > 0 %}
          {% for note in photo_notes %}
            <div class="photo-card">
              <h3><a class="internal-link" href="{{ site.baseurl }}{{ note.url }}">{{ note.title }}</a></h3>
              <small class="photo-date">{{ note.date | date: "%Y-%m-%d" }}</small>
            </div>
          {% endfor %}
        {% else %}
          <p class="empty-state">사진이 준비되면 여기에 표시됩니다.</p>
        {% endif %}
      </div>
    </section>

    <!-- 음악 섹션 -->
    <section id="music" class="content-section">
      <h1>🎵 음악</h1>
      <p>좋아하는 음악과 음악에 대한 생각들을 정리한 공간입니다.</p>
      
      <div class="music-grid">
        {% assign music_notes = site.notes | where_exp: "note", "note.path contains '/music/'" | sort: "date" | reverse %}
        {% if music_notes.size > 0 %}
          {% for note in music_notes %}
            <div class="music-card">
              <h3><a class="internal-link" href="{{ site.baseurl }}{{ note.url }}">{{ note.title }}</a></h3>
              <small class="music-date">{{ note.date | date: "%Y-%m-%d" }}</small>
            </div>
          {% endfor %}
        {% else %}
          <p class="empty-state">음악 관련 포스트가 준비되면 여기에 표시됩니다.</p>
        {% endif %}
      </div>
    </section>

    <!-- 영상 섹션 -->
    <section id="videos" class="content-section">
      <h1>🎬 영상</h1>
      <p>영화, 드라마, 다큐멘터리 등 시청한 영상 콘텐츠에 대한 리뷰와 생각들입니다.</p>
      
      <div class="videos-grid">
        {% assign video_notes = site.notes | where_exp: "note", "note.path contains '/videos/'" | sort: "date" | reverse %}
        {% if video_notes.size > 0 %}
          {% for note in video_notes %}
            <div class="video-card">
              <h3><a class="internal-link" href="{{ site.baseurl }}{{ note.url }}">{{ note.title }}</a></h3>
              <small class="video-date">{{ note.date | date: "%Y-%m-%d" }}</small>
            </div>
          {% endfor %}
        {% else %}
          <p class="empty-state">영상 관련 포스트가 준비되면 여기에 표시됩니다.</p>
        {% endif %}
      </div>
    </section>
  </main>
</div>

<style>
  .main-container {
    display: flex;
    min-height: 100vh;
    gap: 2rem;
  }

  .sidebar-nav {
    width: 200px;
    flex-shrink: 0;
    padding: 2rem 1rem;
    background: #f8f9fa;
    border-radius: 8px;
    height: fit-content;
    position: sticky;
    top: 2rem;
  }

  .nav-menu {
    list-style: none;
    padding: 0;
    margin: 0;
  }

  .nav-menu li {
    margin-bottom: 0.5rem;
  }

  .nav-link {
    display: block;
    padding: 0.75rem 1rem;
    text-decoration: none;
    color: #666;
    border-radius: 6px;
    transition: all 0.2s ease;
    font-weight: 500;
  }

  .nav-link:hover {
    background: #e9ecef;
    color: #333;
    transform: translateX(4px);
  }

  .nav-link.active {
    background: #007acc;
    color: white;
  }

  .content-area {
    flex: 1;
    padding: 2rem 0;
  }

  .content-section {
    display: none;
    animation: fadeIn 0.3s ease;
  }

  .content-section.active {
    display: block;
  }

  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(10px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .intro-text {
    font-size: 1.1rem;
    line-height: 1.6;
    color: #555;
    margin-bottom: 2rem;
    padding: 1.5rem;
    background: #f0f8ff;
    border-radius: 8px;
    border-left: 4px solid #007acc;
  }

  .recent-updates {
    background: #fff;
    border: 1px solid #e9ecef;
    border-radius: 8px;
    padding: 1.5rem;
    margin-top: 2rem;
  }

  .recent-updates h3 {
    margin-top: 0;
    color: #333;
  }

  .books-grid, .photos-grid, .music-grid, .videos-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 1.5rem;
    margin-top: 2rem;
  }

  .book-card, .photo-card, .music-card, .video-card {
    background: #fff;
    border: 1px solid #e9ecef;
    border-radius: 8px;
    padding: 1.5rem;
    transition: transform 0.2s ease, box-shadow 0.2s ease;
  }

  .book-card:hover, .photo-card:hover, .music-card:hover, .video-card:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  }

  .book-card h3, .photo-card h3, .music-card h3, .video-card h3 {
    margin-top: 0;
    margin-bottom: 0.5rem;
  }

  .book-author {
    color: #666;
    font-style: italic;
    margin-bottom: 0.5rem;
  }

  .book-excerpt {
    color: #777;
    font-size: 0.9rem;
    line-height: 1.5;
  }

  .book-date, .photo-date, .music-date, .video-date {
    color: #999;
    font-size: 0.8rem;
  }

  .empty-state {
    color: #999;
    font-style: italic;
    text-align: center;
    padding: 2rem;
    background: #f8f9fa;
    border-radius: 8px;
    border: 1px dashed #ddd;
  }

  .internal-link {
    color: #007acc;
    text-decoration: none;
  }

  .internal-link:hover {
    text-decoration: underline;
  }

  /* 반응형 디자인 */
  @media (max-width: 768px) {
    .main-container {
      flex-direction: column;
    }

    .sidebar-nav {
      width: 100%;
      position: static;
      margin-bottom: 2rem;
    }

    .nav-menu {
      display: flex;
      gap: 0.5rem;
      overflow-x: auto;
      padding-bottom: 0.5rem;
    }

    .nav-menu li {
      margin-bottom: 0;
      flex-shrink: 0;
    }

    .nav-link {
      white-space: nowrap;
    }

    .books-grid, .photos-grid, .music-grid, .videos-grid {
      grid-template-columns: 1fr;
    }
  }

  .wrapper {
    max-width: none;
    padding: 1rem;
  }
</style>

<script>
  document.addEventListener('DOMContentLoaded', function() {
    const navLinks = document.querySelectorAll('.nav-link');
    const sections = document.querySelectorAll('.content-section');

    navLinks.forEach(link => {
      link.addEventListener('click', function(e) {
        e.preventDefault();
        
        // 활성 링크 변경
        navLinks.forEach(l => l.classList.remove('active'));
        this.classList.add('active');
        
        // 활성 섹션 변경
        sections.forEach(s => s.classList.remove('active'));
        const targetSection = document.getElementById(this.dataset.section);
        if (targetSection) {
          targetSection.classList.add('active');
        }
      });
    });
  });
</script>