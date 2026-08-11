<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>SABINEX Dashboard</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: Inter, Arial, sans-serif;
    }

    body {
      background: #f6f8fa;
      color: #1f2328;
    }

    .app {
      display: flex;
      min-height: 100vh;
    }

    .sidebar {
      width: 250px;
      background: #0d1117;
      color: white;
      padding: 24px 18px;
      position: fixed;
      left: 0;
      top: 0;
      bottom: 0;
    }

    .brand {
      font-size: 24px;
      font-weight: 800;
      margin-bottom: 6px;
    }

    .tagline {
      font-size: 12px;
      color: #8b949e;
      line-height: 1.5;
      margin-bottom: 30px;
    }

    .menu {
      display: flex;
      flex-direction: column;
      gap: 8px;
    }

    .menu a {
      color: #c9d1d9;
      text-decoration: none;
      padding: 11px 13px;
      border-radius: 7px;
      font-size: 14px;
      transition: .2s;
    }

    .menu a:hover,
    .menu a.active {
      background: #21262d;
      color: white;
    }

    .main {
      margin-left: 250px;
      width: calc(100% - 250px);
    }

    .topbar {
      height: 70px;
      background: white;
      border-bottom: 1px solid #d0d7de;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 0 28px;
      position: sticky;
      top: 0;
      z-index: 5;
    }

    .search {
      width: 320px;
      padding: 10px 14px;
      border: 1px solid #d0d7de;
      border-radius: 8px;
      outline: none;
    }

    .profile-mini {
      display: flex;
      align-items: center;
      gap: 10px;
      font-size: 14px;
      font-weight: 600;
    }

    .avatar {
      width: 36px;
      height: 36px;
      background: #0969da;
      border-radius: 50%;
      color: white;
      display: flex;
      justify-content: center;
      align-items: center;
      font-weight: 700;
    }

    .content {
      padding: 28px;
      max-width: 1500px;
      margin: auto;
    }

    h1 {
      font-size: 28px;
      margin-bottom: 4px;
    }

    .subhead {
      color: #656d76;
      margin-bottom: 24px;
    }

    .grid-4 {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 16px;
      margin-bottom: 20px;
    }

    .card {
      background: white;
      border: 1px solid #d0d7de;
      border-radius: 10px;
      padding: 18px;
    }

    .metric-label {
      font-size: 13px;
      color: #656d76;
      margin-bottom: 8px;
    }

    .metric-number {
      font-size: 28px;
      font-weight: 700;
    }

    .metric-small {
      font-size: 12px;
      margin-top: 7px;
      color: #1a7f37;
    }

    .layout-2 {
      display: grid;
      grid-template-columns: 2fr 1fr;
      gap: 18px;
      margin-bottom: 20px;
    }

    .card-title {
      font-size: 16px;
      font-weight: 700;
      margin-bottom: 14px;
    }

    .contribution-info {
      font-size: 13px;
      color: #656d76;
      margin-bottom: 12px;
    }

    .contribution-grid {
      display: grid;
      grid-template-columns: repeat(26, 1fr);
      gap: 4px;
    }

    .box {
      aspect-ratio: 1;
      border-radius: 3px;
      background: #ebedf0;
    }

    .level-1 { background: #9be9a8; }
    .level-2 { background: #40c463; }
    .level-3 { background: #30a14e; }
    .level-4 { background: #216e39; }

    .level-box {
      margin-top: 14px;
    }

    .level-title {
      font-size: 13px;
      color: #656d76;
    }

    .level-name {
      font-size: 22px;
      font-weight: 700;
      margin: 5px 0;
    }

    .progress {
      height: 9px;
      background: #d8dee4;
      border-radius: 20px;
      overflow: hidden;
    }

    .progress-bar {
      height: 100%;
      width: 72%;
      background: #0969da;
    }

    .progress-text {
      font-size: 12px;
      color: #656d76;
      margin-top: 8px;
    }

    .experience-item,
    .activity-item,
    .leader-item {
      border-bottom: 1px solid #d8dee4;
      padding: 13px 0;
    }

    .experience-item:last-child,
    .activity-item:last-child,
    .leader-item:last-child {
      border-bottom: 0;
    }

    .experience-title {
      font-weight: 650;
      margin-bottom: 5px;
    }

    .experience-meta {
      font-size: 12px;
      color: #656d76;
    }

    .activity-item {
      font-size: 13px;
      line-height: 1.5;
    }

    .activity-time {
      display: block;
      font-size: 11px;
      color: #8c959f;
      margin-top: 3px;
    }

    .leader-item {
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .leader-left {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .rank {
      font-weight: 700;
      width: 25px;
    }

    .leader-name {
      font-weight: 600;
      font-size: 13px;
    }

    .leader-school {
      font-size: 11px;
      color: #656d76;
    }

    .points {
      font-weight: 700;
      font-size: 13px;
    }

    .insight-grid {
      display: grid;
      grid-template-columns: repeat(5, 1fr);
      gap: 10px;
    }

    .interest {
      padding: 14px;
      border: 1px solid #d0d7de;
      border-radius: 8px;
      text-align: center;
    }

    .interest-name {
      font-size: 12px;
      color: #656d76;
      margin-bottom: 5px;
    }

    .interest-value {
      font-size: 22px;
      font-weight: 700;
    }

    .badge-row {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
    }

    .badge {
      padding: 7px 10px;
      border-radius: 20px;
      background: #ddf4ff;
      color: #0969da;
      font-size: 12px;
      font-weight: 600;
      border: 1px solid #b6e3ff;
    }

    @media (max-width: 1100px) {
      .grid-4 {
        grid-template-columns: repeat(2, 1fr);
      }

      .layout-2 {
        grid-template-columns: 1fr;
      }

      .insight-grid {
        grid-template-columns: repeat(2, 1fr);
      }
    }

    @media (max-width: 700px) {
      .sidebar {
        display: none;
      }

      .main {
        margin-left: 0;
        width: 100%;
      }

      .grid-4 {
        grid-template-columns: 1fr;
      }

      .search {
        width: 180px;
      }

      .content {
        padding: 18px;
      }
    }
  </style>
</head>

<body>
<div class="app">

  <aside class="sidebar">
    <div class="brand">SABINEX</div>
    <div class="tagline">
      SATU BK Network & Experience<br>
      Connecting Counselors. Enriching Student Experiences.
    </div>

    <div class="menu">
      <a href="#" class="active">⌂ Overview</a>
      <a href="#">👤 Profile</a>
      <a href="#">👥 Students</a>
      <a href="#">🏫 Schools</a>
      <a href="#">✨ Experiences</a>
      <a href="#">💬 Consultations</a>
      <a href="#">🌐 Network</a>
      <a href="#">⭐ Points</a>
      <a href="#">🎁 Rewards</a>
      <a href="#">📊 Insights</a>
      <a href="#">⚙ Settings</a>
    </div>
  </aside>

  <main class="main">

    <header class="topbar">
      <input
        class="search"
        type="text"
        placeholder="Search students, schools, counselors..."
      >

      <div class="profile-mini">
        <div class="avatar">SA</div>
        SABINEX Admin
      </div>
    </header>

    <section class="content">

      <h1>SABINEX Overview</h1>
      <p class="subhead">
        Counselor Network & Student Experience Dashboard
      </p>

      <div class="grid-4">

        <div class="card">
          <div class="metric-label">Counselors Connected</div>
          <div class="metric-number">428</div>
          <div class="metric-small">↑ 18% this month</div>
        </div>

        <div class="card">
          <div class="metric-label">Schools Connected</div>
          <div class="metric-number">176</div>
          <div class="metric-small">+12 new schools</div>
        </div>

        <div class="card">
          <div class="metric-label">Active Students</div>
          <div class="metric-number">8,420</div>
          <div class="metric-small">+1,248 this month</div>
        </div>

        <div class="card">
          <div class="metric-label">Student Experiences</div>
          <div class="metric-number">1,284</div>
          <div class="metric-small">↑ 26% engagement</div>
        </div>

      </div>


      <div class="layout-2">

        <div class="card">
          <div class="card-title">Contribution Activity</div>

          <div class="contribution-info">
            842 student-impact contributions in the last year
          </div>

          <div class="contribution-grid" id="contributionGrid"></div>
        </div>

        <div class="card">
          <div class="card-title">Counselor Level</div>

          <div class="level-box">
            <div class="level-title">Current level</div>
            <div class="level-name">Champion</div>

            <div class="progress">
              <div class="progress-bar"></div>
            </div>

            <div class="progress-text">
              4,280 / 5,000 points — 720 points to Counselor Fellow
            </div>
          </div>

          <br>

          <div class="card-title">Badges</div>

          <div class="badge-row">
            <div class="badge">Career Mentor</div>
            <div class="badge">Network Builder</div>
            <div class="badge">Student Advocate</div>
            <div class="badge">Early Adopter</div>
          </div>
        </div>

      </div>


      <div class="layout-2">

        <div class="card">
          <div class="card-title">Recent Experiences</div>

          <div class="experience-item">
            <div class="experience-title">Career Mapping 2026</div>
            <div class="experience-meta">
              SMAN 1 Tulungagung • 146 students • Completed
            </div>
          </div>

          <div class="experience-item">
            <div class="experience-title">Mental Health Check-in</div>
            <div class="experience-meta">
              MAN 2 Tulungagung • 83 students • Active
            </div>
          </div>

          <div class="experience-item">
            <div class="experience-title">Campus Experience Day</div>
            <div class="experience-meta">
              UIN SATU • 112 students • Upcoming
            </div>
          </div>

          <div class="experience-item">
            <div class="experience-title">Try Your Major</div>
            <div class="experience-meta">
              Multi-school • 68 students • Completed
            </div>
          </div>

        </div>


        <div class="card">
          <div class="card-title">Recent Activity</div>

          <div class="activity-item">
            <strong>32 students</strong> completed Career Fit Screening.
            <span class="activity-time">10 minutes ago</span>
          </div>

          <div class="activity-item">
            Ahmad Fauzi earned
            <strong>Student Advocate</strong> badge.
            <span class="activity-time">45 minutes ago</span>
          </div>

          <div class="activity-item">
            SMAN 3 Trenggalek joined SABINEX Network.
            <span class="activity-time">2 hours ago</span>
          </div>

          <div class="activity-item">
            12 new counseling sessions were completed.
            <span class="activity-time">Today</span>
          </div>

        </div>

      </div>


      <div class="card" style="margin-bottom:20px;">

        <div class="card-title">Student Interest Insights</div>

        <div class="insight-grid">

          <div class="interest">
            <div class="interest-name">Psychology</div>
            <div class="interest-value">28%</div>
          </div>

          <div class="interest">
            <div class="interest-name">Business</div>
            <div class="interest-value">24%</div>
          </div>

          <div class="interest">
            <div class="interest-name">Education</div>
            <div class="interest-value">19%</div>
          </div>

          <div class="interest">
            <div class="interest-name">Technology</div>
            <div class="interest-value">17%</div>
          </div>

          <div class="interest">
            <div class="interest-name">Communication</div>
            <div class="interest-value">12%</div>
          </div>

        </div>

      </div>


      <div class="layout-2">

        <div class="card">
          <div class="card-title">SABINEX Impact Board</div>

          <div class="leader-item">
            <div class="leader-left">
              <div class="rank">🥇</div>
              <div>
                <div class="leader-name">Ahmad Fauzi</div>
                <div class="leader-school">SMAN 1 Tulungagung</div>
              </div>
            </div>
            <div class="points">4,820 pts</div>
          </div>

          <div class="leader-item">
            <div class="leader-left">
              <div class="rank">🥈</div>
              <div>
                <div class="leader-name">Siti Rahma</div>
                <div class="leader-school">MAN 2 Tulungagung</div>
              </div>
            </div>
            <div class="points">4,560 pts</div>
          </div>

          <div class="leader-item">
            <div class="leader-left">
              <div class="rank">🥉</div>
              <div>
                <div class="leader-name">Budi Santoso</div>
                <div class="leader-school">SMKN 1 Blitar</div>
              </div>
            </div>
            <div class="points">4,310 pts</div>
          </div>

          <div class="leader-item">
            <div class="leader-left">
              <div class="rank">4</div>
              <div>
                <div class="leader-name">Nur Aini</div>
                <div class="leader-school">SMAN 2 Kediri</div>
              </div>
            </div>
            <div class="points">3,980 pts</div>
          </div>

        </div>


        <div class="card">
          <div class="card-title">Network Snapshot</div>

          <div class="experience-item">
            <div class="metric-label">Student Screening Completion</div>
            <div class="metric-number">68%</div>
          </div>

          <div class="experience-item">
            <div class="metric-label">Students Need Guidance</div>
            <div class="metric-number">1,218</div>
          </div>

          <div class="experience-item">
            <div class="metric-label">Consultations Completed</div>
            <div class="metric-number">638</div>
          </div>

          <div class="experience-item">
            <div class="metric-label">Active Counselor Rate</div>
            <div class="metric-number">82%</div>
          </div>

        </div>

      </div>

    </section>
  </main>

</div>


<script>
  const grid = document.getElementById("contributionGrid");

  for (let i = 0; i < 182; i++) {
    const box = document.createElement("div");

    const random = Math.random();

    box.className = "box";

    if (random > 0.84) {
      box.classList.add("level-4");
    } else if (random > 0.68) {
      box.classList.add("level-3");
    } else if (random > 0.50) {
      box.classList.add("level-2");
    } else if (random > 0.35) {
      box.classList.add("level-1");
    }

    box.title = "Student Impact Activity";

    grid.appendChild(box);
  }
</script>

</body>
</html>
