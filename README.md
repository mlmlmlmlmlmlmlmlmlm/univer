<!DOCTYPE html>
<html lang="kk">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="theme-color" content="#f8e4e9">
  <title>Жасмин · Тұсаукесерге шақырту</title>

  <style>
    :root {
      --pink: #f8e4e9;
      --cream: #fffaf6;
      --rose: #aa5870;
      --text: #68434d;
      --gold: #b59462;
    }

    * {
      box-sizing: border-box;
    }

    html {
      scroll-behavior: smooth;
    }

    body {
      margin: 0;
      background: #efdee3;
      color: var(--text);
      font-family: Georgia, "Times New Roman", serif;
    }

    body.locked {
      overflow: hidden;
    }

    button {
      font: inherit;
      cursor: pointer;
      -webkit-tap-highlight-color: transparent;
    }

    button:focus-visible,
    a:focus-visible {
      outline: 3px solid var(--rose);
      outline-offset: 5px;
    }

    .page {
      width: 100%;
      max-width: 620px;
      margin: auto;
      overflow: hidden;
      background: var(--cream);
      box-shadow: 0 0 70px #79485518;
    }

    /* Алғаш ашылғандағы мұқаба */
    .welcome {
      position: fixed;
      inset: 0;
      z-index: 100;
      display: grid;
      place-items: center;
      padding: 24px;
      background:
        radial-gradient(circle at 15% 15%, #ffffff 0, transparent 40%),
        linear-gradient(145deg, #faedf0, #efd0db);
      transition: opacity 0.7s, visibility 0.7s;
    }

    .welcome.hidden {
      opacity: 0;
      visibility: hidden;
      pointer-events: none;
    }

    .welcome-card {
      width: min(100%, 380px);
      padding: 60px 25px 45px;
      border: 1px solid #bd9b6b80;
      border-radius: 190px 190px 18px 18px;
      background: #fffaf6d9;
      text-align: center;
    }

    .welcome-name {
      margin: 22px 0;
      color: var(--rose);
      font-size: clamp(48px, 13vw, 70px);
      font-style: italic;
      font-weight: normal;
    }

    .eyebrow {
      font-family: Arial, sans-serif;
      font-size: 10px;
      line-height: 1.8;
      letter-spacing: 3px;
      text-transform: uppercase;
    }

    .open-button {
      margin-top: 25px;
      padding: 17px 28px;
      border: 0;
      border-radius: 40px;
      background: var(--rose);
      color: white;
      box-shadow: 0 8px 25px #aa587030;
    }

    .welcome-card p {
      font-size: 20px;
      line-height: 1.7;
    }

    .ornament {
      color: var(--gold);
      font-size: 32px;
    }

    /* Негізгі сурет */
    .hero {
      position: relative;
      height: 100svh;
      min-height: 730px;
      max-height: 1000px;
      background: var(--pink);
    }

    .hero-image {
      position: absolute;
      inset: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
      object-position: center 30%;
    }

    .hero::after {
      content: "";
      position: absolute;
      inset: 0;
      background: linear-gradient(
        to bottom,
        #5130400a 0%,
        transparent 40%,
        #fffaf699 66%,
        #fffaf6f5 88%,
        var(--cream) 100%
      );
    }

    .hero-content {
      position: absolute;
      z-index: 1;
      right: 20px;
      bottom: 35px;
      left: 20px;
      text-align: center;
    }

    .hero-label {
      display: inline-block;
      padding: 8px 18px;
      border: 1px solid #ffffff90;
      border-radius: 30px;
      background: #fffaf6cf;
    }

    h1 {
      margin: 20px 0 12px;
      color: var(--rose);
      font-size: clamp(68px, 17vw, 110px);
      font-weight: normal;
      font-style: italic;
      line-height: 1.1;
    }

    .hero-subtitle {
      font-size: 23px;
      letter-spacing: 2px;
    }

    .date-line {
      margin-top: 25px;
      font-family: Arial, sans-serif;
      font-size: 13px;
      line-height: 1.8;
      letter-spacing: 4px;
    }

    .scroll-link {
      display: inline-block;
      margin-top: 20px;
      color: var(--rose);
      font-size: 30px;
      text-decoration: none;
      animation: bounce 2s infinite;
    }

    /* Мәтін бөлімдері */
    .section {
      padding: 60px 28px;
      text-align: center;
    }

    h2 {
      margin: 18px 0 25px;
      font-size: clamp(28px, 7vw, 38px);
      font-weight: normal;
      line-height: 1.3;
    }

    p {
      margin: 18px 0;
      font-size: 21px;
      line-height: 1.85;
    }

    .invitation {
      background:
        radial-gradient(ellipse at left, #f5dce480, transparent 65%),
        var(--cream);
    }

    .invitation strong {
      color: var(--rose);
    }

    .number-one {
      margin-top: 30px;
      color: var(--rose);
      font-size: 100px;
      font-style: italic;
      line-height: 1;
    }

    .small-label {
      margin-top: 12px;
      font-family: Arial, sans-serif;
      font-size: 10px;
      line-height: 1.8;
      letter-spacing: 3px;
      text-transform: uppercase;
    }

    .photo-section {
      padding: 0 24px 25px;
    }

    .portrait {
      display: block;
      width: 100%;
      height: auto;
      border: 7px solid white;
      border-radius: 240px 240px 18px 18px;
      box-shadow: 0 12px 35px #9c63751a;
    }

    .wish {
      padding: 35px 25px 60px;
      text-align: center;
    }

    .wish p {
      color: var(--rose);
      font-size: 26px;
      font-style: italic;
      line-height: 1.7;
    }

    /* Күнтізбе */
    .event {
      background: linear-gradient(160deg, #f9e9ec, #f2dbe2);
    }

    .event-day {
      margin-top: 22px;
      color: var(--rose);
      font-size: 88px;
      line-height: 1;
    }

    .event-month {
      margin-top: 12px;
      font-size: 26px;
    }

    .event-weekday {
      margin-top: 12px;
      font-size: 16px;
    }

    .calendar {
      display: grid;
      grid-template-columns: repeat(7, 1fr);
      gap: 8px;
      max-width: 350px;
      margin: 30px auto;
      font-family: Arial, sans-serif;
      font-size: 14px;
    }

    .calendar span {
      display: grid;
      place-items: center;
      aspect-ratio: 1;
    }

    .calendar .weekday {
      color: #9d7885;
      font-size: 10px;
    }

    .calendar .selected {
      border-radius: 50%;
      background: var(--rose);
      color: white;
      box-shadow: 0 0 0 5px #aa58701c;
    }

    .event-time {
      display: inline-block;
      margin: 10px 0 20px;
      padding: 18px 35px;
      border-top: 1px solid #b5946280;
      border-bottom: 1px solid #b5946280;
      font-size: 28px;
    }

    /* Кері санақ */
    .countdown {
      display: flex;
      justify-content: center;
      gap: 10px;
      margin-top: 25px;
    }

    .countdown-item {
      flex: 1;
      max-width: 100px;
      padding: 17px 3px;
      border: 1px solid #ffffffb0;
      border-radius: 15px;
      background: #fffaf680;
    }

    .countdown-item b {
      display: block;
      color: var(--rose);
      font-size: clamp(28px, 8vw, 40px);
      font-weight: normal;
      font-variant-numeric: tabular-nums;
    }

    .countdown-item span {
      display: block;
      margin-top: 8px;
      font-family: Arial, sans-serif;
      font-size: 9px;
      letter-spacing: 1px;
    }

    .count-status {
      font-size: 16px;
    }

    .address {
      font-size: 25px;
      line-height: 1.8;
    }

    .closing {
      padding-bottom: 100px;
      background: linear-gradient(var(--cream), #f3d8e1);
    }

    .heart {
      color: var(--rose);
      font-size: 38px;
    }

    /* Музыка */
    .music-button {
      position: fixed;
      z-index: 50;
      right: 18px;
      bottom: 20px;
      display: grid;
      place-items: center;
      width: 56px;
      height: 56px;
      border: 1px solid #ffffffc0;
      border-radius: 50%;
      background: #fffaf6ee;
      color: var(--rose);
      font-size: 25px;
      box-shadow: 0 5px 25px #68434d25;
    }

    .music-button.playing {
      animation: rotate 8s linear infinite;
    }

    .music-status {
      position: fixed;
      z-index: 51;
      right: 18px;
      bottom: 88px;
      max-width: 270px;
      padding: 14px 17px;
      border: 1px solid #e6c4cf;
      border-radius: 14px;
      background: var(--cream);
      color: var(--text);
      font-family: Arial, sans-serif;
      font-size: 13px;
      line-height: 1.6;
      box-shadow: 0 5px 25px #68434d15;
    }

    .music-status[hidden] {
      display: none;
    }

    /* Бөлімдердің пайда болуы */
    .reveal {
      opacity: 1;
    }

    .js .reveal {
      opacity: 0;
      transform: translateY(25px);
      transition: opacity 0.8s ease, transform 0.8s ease;
    }

    .js .reveal.visible {
      opacity: 1;
      transform: translateY(0);
    }

    @keyframes bounce {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(8px); }
    }

    @keyframes rotate {
      to { transform: rotate(360deg); }
    }

    @media (min-width: 621px) {
      .music-button {
        right: calc((100vw - 620px) / 2 + 18px);
      }

      .music-status {
        right: calc((100vw - 620px) / 2 + 18px);
      }
    }

    @media (prefers-reduced-motion: reduce) {
      html { scroll-behavior: auto; }

      *, *::before, *::after {
        animation: none !important;
        transition: none !important;
      }

      .js .reveal {
        opacity: 1;
        transform: none;
      }
    }
  </style>
</head>

<body>
  <!-- Ашылатын шақырту -->
  <div class="welcome" id="welcome">
    <div class="welcome-card">
      <div class="ornament">❦</div>
      <div class="eyebrow">Сізге арналған шақырту</div>
      <h2 class="welcome-name">Жасмин</h2>
      <p>Кішкентай қадам —<br>үлкен қуаныш!</p>
      <div class="small-label">1 жас · Тұсаукесер</div>

      <button class="open-button" id="openButton">
        Шақыртуды ашу ♡
      </button>
    </div>
  </div>

  <main class="page">
    <!-- Бірінші фото -->
    <header class="hero">
      <img
        class="hero-image"
        src="1.jpg"
        alt="Қызғылт көйлек киген Жасмин"
        fetchpriority="high"
      >

      <div class="hero-content">
        <div class="hero-label eyebrow">
          Біздің кішкентай ханшайым
        </div>

        <h1>Жасмин</h1>

        <div class="hero-subtitle">1 жас · Тұсаукесер</div>
        <div class="date-line">01 · 11 · 2026</div>

        <a
          class="scroll-link"
          href="#invitation"
          aria-label="Шақырту мәтініне өту"
        >↓</a>
      </div>
    </header>

    <!-- Шақырту мәтіні -->
    <section class="section invitation" id="invitation">
      <div class="reveal">
        <div class="ornament">❦</div>
        <h2>Құрметті қонақтар!</h2>

        <p>
          Сіздерді сүйікті қызымыз
          <strong>Жасминнің</strong>
          1 жасқа толуына арналған тұсаукесер
          дастарханының қадірлі қонағы
          болуға шақырамыз!
        </p>

        <p>
          Алғашқы қадамына ақ тілек айтып,
          қуанышымызды бірге бөлісіңіздер!
        </p>

        <div class="number-one">1</div>
        <div class="small-label">Бақытқа толы бір жас</div>
      </div>
    </section>

    <!-- Екінші фото -->
    <section class="photo-section">
      <img
        class="portrait reveal"
        src="2.jpg"
        alt="Жасминнің портреті"
        loading="lazy"
      >
    </section>

    <section class="wish">
      <div class="reveal">
        <div class="ornament">❦</div>
        <p>
          Қаз-қаз басқан қадамың,<br>
          Қуанышқа толсын әр таңың!
        </p>
      </div>
    </section>

    <!-- Той күні -->
    <section class="section event">
      <div class="reveal">
        <div class="eyebrow">Қуанышты күн</div>
        <div class="event-day">01</div>
        <div class="event-month">Қараша · 2026</div>
        <div class="event-weekday">Жексенбі</div>

        <div
          class="calendar"
          id="calendar"
          aria-label="2026 жылғы қараша күнтізбесі"
        ></div>

        <div class="event-time">Сағат 13:00</div>

        <p>Тойымызға дейін:</p>

        <div
          class="countdown"
          role="timer"
          aria-label="Тойға дейін қалған уақыт"
        >
          <div class="countdown-item">
            <b id="days">00</b>
            <span>КҮН</span>
          </div>

          <div class="countdown-item">
            <b id="hours">00</b>
            <span>САҒАТ</span>
          </div>

          <div class="countdown-item">
            <b id="minutes">00</b>
            <span>МИНУТ</span>
          </div>

          <div class="countdown-item">
            <b id="seconds">00</b>
            <span>СЕКУНД</span>
          </div>
        </div>

        <p class="count-status" id="countStatus"></p>
      </div>
    </section>

    <!-- Мекенжай -->
    <section class="section">
      <div class="reveal">
        <div class="ornament">❦</div>
        <h2>Мекенжайымыз</h2>

        <p class="address">
          Үмбетәлі ауылы<br>
          Мұсабайев көшесі, 77в
        </p>
      </div>
    </section>

    <!-- Үшінші фото -->
    <section class="photo-section">
      <img
        class="portrait reveal"
        src="3.jpg"
        alt="Күлімдеп отырған Жасмин"
        loading="lazy"
      >
    </section>

    <footer class="section closing">
      <div class="reveal">
        <div class="heart">♡</div>
        <h2>Сіздерді күтеміз!</h2>

        <p>
          Жасминнің алғашқы қадамына<br>
          бірге куә болайық!
        </p>

        <div class="date-line">
          01 · 11 · 2026<br>13:00
        </div>
      </div>
    </footer>
  </main>

  <!-- ADIL — «Қызым»: MP3 файлын қасына салыңыз -->
  <audio id="music" loop preload="none">
    <source src="qyzym.mp3" type="audio/mpeg">
  </audio>

  <button
    class="music-button"
    id="musicButton"
    aria-label="Музыканы қосу"
    aria-pressed="false"
  >♫</button>

  <div
    class="music-status"
    id="musicStatus"
    role="status"
    hidden
  ></div>

  <script>
    document.documentElement.classList.add("js");
    document.body.classList.add("locked");

    const welcome = document.getElementById("welcome");
    const openButton = document.getElementById("openButton");
    const music = document.getElementById("music");
    const musicButton = document.getElementById("musicButton");
    const musicStatus = document.getElementById("musicStatus");

    let statusTimeout;

    function showMusicStatus(text) {
      clearTimeout(statusTimeout);
      musicStatus.textContent = text;
      musicStatus.hidden = false;

      statusTimeout = setTimeout(() => {
        musicStatus.hidden = true;
      }, 5000);
    }

    function updateMusicButton() {
      const playing = !music.paused;

      musicButton.classList.toggle("playing", playing);
      musicButton.setAttribute("aria-pressed", String(playing));
      musicButton.setAttribute(
        "aria-label",
        playing ? "Музыканы өшіру" : "Музыканы қосу"
      );
    }

    async function playMusic(showError = true) {
      try {
        music.volume = 0.65;
        await music.play();
        musicStatus.hidden = true;
      } catch (error) {
        if (showError) {
          showMusicStatus(
            "Музыка ашылмады. qyzym.mp3 файлы жүктелгенін тексеріңіз."
          );
        }
      }

      updateMusicButton();
    }

    openButton.addEventListener("click", () => {
      welcome.classList.add("hidden");
      document.body.classList.remove("locked");

      // Батырма басылғаннан кейін музыка қосылады.
      playMusic();

      setTimeout(() => {
        welcome.remove();
        document.querySelector(".scroll-link").focus({
          preventScroll: true
        });
      }, 750);
    });

    musicButton.addEventListener("click", () => {
      if (music.paused) {
        playMusic();
      } else {
        music.pause();
      }
    });

    music.addEventListener("play", updateMusicButton);
    music.addEventListener("pause", updateMusicButton);

    // Қараша 2026: 1 қараша — жексенбі.
    const calendar = document.getElementById("calendar");
    const weekdays = ["ДС", "СС", "СР", "БС", "ЖМ", "СБ", "ЖС"];

    weekdays.forEach((day) => {
      const cell = document.createElement("span");
      cell.className = "weekday";
      cell.textContent = day;
      calendar.appendChild(cell);
    });

    for (let i = 0; i < 6; i++) {
      const emptyCell = document.createElement("span");
      emptyCell.setAttribute("aria-hidden", "true");
      calendar.appendChild(emptyCell);
    }

    for (let day = 1; day <= 30; day++) {
      const cell = document.createElement("span");
      cell.textContent = day;

      if (day === 1) {
        cell.className = "selected";
        cell.setAttribute("aria-label", "1 қараша — той күні");
      }

      calendar.appendChild(cell);
    }

    // Қазақстан уақыты: UTC+5.
    const eventTime = new Date(
      "2026-11-01T13:00:00+05:00"
    ).getTime();

    const counterElements = [
      document.getElementById("days"),
      document.getElementById("hours"),
      document.getElementById("minutes"),
      document.getElementById("seconds")
    ];

    function updateCountdown() {
      const remaining = Math.max(0, eventTime - Date.now());

      const values = [
        Math.floor(remaining / 86400000),
        Math.floor(remaining / 3600000) % 24,
        Math.floor(remaining / 60000) % 60,
        Math.floor(remaining / 1000) % 60
      ];

      counterElements.forEach((element, index) => {
        element.textContent = String(values[index]).padStart(2, "0");
      });

      if (remaining === 0) {
        document.getElementById("countStatus").textContent =
          "Көптен күткен қуанышты күн келді!";
      }
    }

    updateCountdown();
    setInterval(updateCountdown, 1000);

    // Төмен сырғытқанда бөлімдер біртіндеп көрінеді.
    const revealElements = document.querySelectorAll(".reveal");

    if ("IntersectionObserver" in window) {
      const observer = new IntersectionObserver(
        (entries) => {
          entries.forEach((entry) => {
            if (entry.isIntersecting) {
              entry.target.classList.add("visible");
              observer.unobserve(entry.target);
            }
          });
        },
        { threshold: 0.08 }
      );

      revealElements.forEach((element) => {
        observer.observe(element);
      });
    } else {
      revealElements.forEach((element) => {
        element.classList.add("visible");
      });
    }
  </script>

  <noscript>
    <style>
      .welcome { display: none; }
      body { overflow: auto !important; }
    </style>
  </noscript>
</body>
</html>
