<!DOCTYPE html>
<html lang="uz">
<head>
  <meta charset="UTF-8">
  <meta name="viewport"
        content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">

  <title>Music</title>

  <script src="https://telegram.org/js/telegram-web-app.js"></script>

  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      background: #09090d;
      color: #fff;
      font-family: -apple-system, BlinkMacSystemFont, Arial, sans-serif;
      padding-bottom: 120px;
    }

    header {
      padding: 24px 18px 10px;
    }

    header h1 {
      font-size: 28px;
    }

    header p {
      color: #85858f;
      margin-top: 5px;
    }

    .search {
      padding: 12px 18px;
    }

    .search input {
      width: 100%;
      height: 48px;
      border: 0;
      outline: none;
      border-radius: 15px;
      background: #18181e;
      color: white;
      padding: 0 16px;
      font-size: 15px;
    }

    .section {
      padding: 14px 18px;
    }

    .title {
      font-size: 20px;
      margin-bottom: 14px;
    }

    .playlists {
      display: flex;
      gap: 14px;
      overflow-x: auto;
      scrollbar-width: none;
    }

    .playlists::-webkit-scrollbar {
      display: none;
    }

    .playlist {
      min-width: 145px;
    }

    .playlist img {
      width: 145px;
      height: 145px;
      object-fit: cover;
      border-radius: 16px;
    }

    .playlist h3 {
      font-size: 14px;
      margin-top: 8px;
    }

    .playlist p {
      color: #85858f;
      font-size: 12px;
      margin-top: 4px;
    }

    .song {
      display: flex;
      align-items: center;
      gap: 12px;
      padding: 9px 0;
    }

    .song-cover {
      width: 54px;
      height: 54px;
      border-radius: 12px;
      object-fit: cover;
    }

    .song-info {
      flex: 1;
      min-width: 0;
    }

    .song-info h3 {
      font-size: 15px;
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
    }

    .song-info p {
      color: #85858f;
      font-size: 12px;
      margin-top: 4px;
    }

    .play-btn {
      width: 40px;
      height: 40px;
      border: 0;
      border-radius: 50%;
      background: white;
      color: black;
      font-size: 16px;
    }

    /* PLAYER */

    .player {
      position: fixed;
      left: 10px;
      right: 10px;
      bottom: 78px;
      background: #1b1b22;
      border-radius: 18px;
      padding: 12px;
      display: none;
      z-index: 10;
    }

    .player-top {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .player-cover {
      width: 48px;
      height: 48px;
      border-radius: 10px;
      object-fit: cover;
    }

    .player-info {
      flex: 1;
    }

    .player-info h3 {
      font-size: 14px;
    }

    .player-info p {
      color: #85858f;
      font-size: 11px;
      margin-top: 3px;
    }

    .pause-btn {
      width: 38px;
      height: 38px;
      border: 0;
      border-radius: 50%;
      background: white;
      color: black;
      font-size: 15px;
    }

    .progress {
      width: 100%;
      margin-top: 10px;
    }

    .time {
      display: flex;
      justify-content: space-between;
      color: #777780;
      font-size: 10px;
      margin-top: 3px;
    }

    /* BOTTOM */

    .bottom {
      position: fixed;
      left: 0;
      right: 0;
      bottom: 0;
      height: 68px;
      background: #111116;
      border-top: 1px solid #24242b;
      display: flex;
      justify-content: space-around;
      align-items: center;
      z-index: 20;
    }

    .bottom button {
      border: 0;
      background: transparent;
      color: #777780;
      font-size: 11px;
    }

    .bottom button.active {
      color: white;
    }
  </style>
</head>

<body>

<header>
  <h1>🎧 Music</h1>
  <p>Kayfiyatingga mos musiqa</p>
</header>

<div class="search">
  <input
    id="search"
    type="text"
    placeholder="🔎 Qo‘shiq yoki artist qidirish..."
  >
</div>

<section class="section">

  <h2 class="title">🔥 Playlistlar</h2>

  <div class="playlists">

    <div class="playlist">
      <img src="https://images.unsplash.com/photo-1493225457124-a3eb161ffa5f?w=600">
      <h3>Night Vibes</h3>
      <p>🌙 Kechki vibe</p>
    </div>

    <div class="playlist">
      <img src="https://images.unsplash.com/photo-1470229722913-7c0e2dbbafd3?w=600">
      <h3>Energy</h3>
      <p>⚡ Energy</p>
    </div>

    <div class="playlist">
      <img src="https://images.unsplash.com/photo-1511379938547-c1f69419868d?w=600">
      <h3>Chill</h3>
      <p>🌌 Relax</p>
    </div>

  </div>

</section>

<section class="section">

  <h2 class="title">🎵 Songs</h2>

  <div id="songs">

    <div
      class="song"
      data-name="Night Drive"
      data-artist="Midnight Artist"
    >

      <img
        class="song-cover"
        src="https://images.unsplash.com/photo-1493225457124-a3eb161ffa5f?w=300"
      >

      <div class="song-info">
        <h3>Night Drive</h3>
        <p>Midnight Artist</p>
      </div>

      <button
        class="play-btn"
        onclick="playSong(0)"
      >
        ▶
      </button>

    </div>


    <div
      class="song"
      data-name="Lost Again"
      data-artist="Dark Vibes"
    >

      <img
        class="song-cover"
        src="https://images.unsplash.com/photo-1470229722913-7c0e2dbbafd3?w=300"
      >

      <div class="song-info">
        <h3>Lost Again</h3>
        <p>Dark Vibes</p>
      </div>

      <button
        class="play-btn"
        onclick="playSong(1)"
      >
        ▶
      </button>

    </div>


    <div
      class="song"
      data-name="After Midnight"
      data-artist="Unknown Artist"
    >

      <img
        class="song-cover"
        src="https://images.unsplash.com/photo-1511379938547-c1f69419868d?w=300"
      >

      <div class="song-info">
        <h3>After Midnight</h3>
        <p>Unknown Artist</p>
      </div>

      <button
        class="play-btn"
        onclick="playSong(2)"
      >
        ▶
      </button>

    </div>

  </div>

</section>


<!-- PLAYER -->

<div class="player" id="player">

  <div class="player-top">

    <img
      id="playerCover"
      class="player-cover"
      src=""
    >

    <div class="player-info">

      <h3 id="playerTitle">Song</h3>
      <p id="playerArtist">Artist</p>

    </div>

    <button
      class="pause-btn"
      onclick="togglePlay()"
      id="pauseButton"
    >
      ▶
    </button>

  </div>

  <input
    class="progress"
    id="progress"
    type="range"
    min="0"
    max="100"
    value="0"
  >

  <div class="time">
    <span id="currentTime">0:00</span>
    <span id="duration">0:00</span>
  </div>

</div>


<!-- NAVIGATION -->

<nav class="bottom">

  <button class="active">
    🏠<br>Home
  </button>

  <button>
    🔎<br>Search
  </button>

  <button>
    ❤️<br>Favorites
  </button>

  <button>
    👤<br>Profile
  </button>

</nav>


<script>

const tg = window.Telegram.WebApp;

tg.ready();
tg.expand();


/*
  AUDIO

  Hozir demo audio URL'lari.
  Keyin o'zingizning qonuniy audio URL'laringizni
  shu joyga qo'yishingiz mumkin.
*/

const songs = [

  {
    title: "Night Drive",
    artist: "Midnight Artist",
    cover: "https://images.unsplash.com/photo-1493225457124-a3eb161ffa5f?w=600",
    audio: "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3"
  },

  {
    title: "Lost Again",
    artist: "Dark Vibes",
    cover: "https://images.unsplash.com/photo-1470229722913-7c0e2dbbafd3?w=600",
    audio: "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-2.mp3"
  },

  {
    title: "After Midnight",
    artist: "Unknown Artist",
    cover: "https://images.unsplash.com/photo-1511379938547-c1f69419868d?w=600",
    audio: "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-3.mp3"
  }

];


const audio = new Audio();

let currentSong = -1;
let playing = false;


function playSong(index) {

  const song = songs[index];

  currentSong = index;

  document.getElementById("player").style.display = "block";

  document.getElementById("playerTitle").innerText =
    song.title;

  document.getElementById("playerArtist").innerText =
    song.artist;

  document.getElementById("playerCover").src =
    song.cover;

  audio.src = song.audio;

  audio.play();

  playing = true;

  document.getElementById("pauseButton").innerText = "⏸";

  tg.HapticFeedback.impactOccurred("light");

}


function togglePlay() {

  if (currentSong === -1) return;

  if (playing) {

    audio.pause();

    playing = false;

    document.getElementById("pauseButton").innerText = "▶";

  } else {

    audio.play();

    playing = true;

    document.getElementById("pauseButton").innerText = "⏸";

  }

}


audio.addEventListener("timeupdate", function() {

  if (!audio.duration) return;

  const percent =
    (audio.currentTime / audio.duration) * 100;

  document.getElementById("progress").value =
    percent;

  document.getElementById("currentTime").innerText =
    formatTime(audio.currentTime);

});


audio.addEventListener("loadedmetadata", function() {

  document.getElementById("duration").innerText =
    formatTime(audio.duration);

});


document.getElementById("progress").addEventListener(
  "input",
  function() {

    if (!audio.duration) return;

    audio.currentTime =
      (this.value / 100) * audio.duration;

  }
);


audio.addEventListener("ended", function() {

  playing = false;

  document.getElementById("pauseButton").innerText =
    "▶";

});


function formatTime(seconds) {

  if (!seconds || isNaN(seconds)) {
    return "0:00";
  }

  const minutes =
    Math.floor(seconds / 60);

  const secs =
    Math.floor(seconds % 60)
      .toString()
      .padStart(2, "0");

  return minutes + ":" + secs;

}


/* SEARCH */

document.getElementById("search")
  .addEventListener("input", function() {

    const query =
      this.value.toLowerCase();

    document.querySelectorAll(".song")
      .forEach(function(song) {

        const name =
          song.dataset.name.toLowerCase();

        const artist =
          song.dataset.artist.toLowerCase();

        if (
          name.includes(query) ||
          artist.includes(query)
        ) {

          song.style.display = "flex";

        } else {

          song.style.display = "none";

        }

      });

  });


</script>

</body>
</html>
