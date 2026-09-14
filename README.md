<!DOCTYPE html>
<html lang="uz">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
<title>GOLD MUSIC</title>
<script src="https://telegram.org/js/telegram-web-app.js"></script>
<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  background: #050505;
  color: #fff;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  min-height: 100vh;
  padding-bottom: 125px;
}
.app {
  max-width: 600px;
  margin: auto;
  padding: 22px 18px;
}
/* HEADER */
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 25px;
}
.logo {
  font-size: 23px;
  font-weight: 800;
  letter-spacing: 2px;
}
.gold {
  color: #d6ad4b;
}
.profile {
  width: 42px;
  height: 42px;
  border: 1px solid #9b7930;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #d6ad4b;
  font-size: 18px;
}
/* SEARCH */
.search {
  width: 100%;
  background: #111;
  border: 1px solid #292929;
  border-radius: 15px;
  padding: 14px 16px;
  color: white;
  outline: none;
  font-size: 15px;
  margin-bottom: 28px;
}
.search:focus {
  border-color: #b89038;
}
.search::placeholder {
  color: #777;
}
/* TITLE */
.section-title {
  font-size: 18px;
  font-weight: 700;
  margin-bottom: 15px;
}
.subtitle {
  color: #777;
  font-size: 13px;
  margin-top: 5px;
}
/* PLAYLISTS */
.playlists {
  display: flex;
  gap: 14px;
  overflow-x: auto;
  padding-bottom: 8px;
  margin-bottom: 28px;
}
.playlists::-webkit-scrollbar {
  display: none;
}
.playlist {
  min-width: 145px;
  height: 165px;
  border-radius: 18px;
  overflow: hidden;
  position: relative;
  border: 1px solid #27200f;
  background: #111;
}
.playlist img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.playlist::after {
  content: "";
  position: absolute;
  inset: 0;
  background: linear-gradient(transparent, rgba(0,0,0,.9));
}
.playlist-name {
  position: absolute;
  bottom: 13px;
  left: 13px;
  z-index: 2;
  font-weight: 700;
}
.playlist-name span {
  display: block;
  color: #d6ad4b;
  font-size: 11px;
  margin-top: 4px;
}
/* SONGS */
.songs {
  display: flex;
  flex-direction: column;
  gap: 10px;
}
.song {
  display: flex;
  align-items: center;
  padding: 9px;
  background: #0d0d0d;
  border: 1px solid #181818;
  border-radius: 15px;
  cursor: pointer;
  transition: .2s;
}
.song:active {
  transform: scale(.98);
}
.song.active {
  border-color: #9b7930;
  background: #14110a;
}
.cover {
  width: 53px;
  height: 53px;
  border-radius: 11px;
  object-fit: cover;
}
.song-info {
  flex: 1;
  margin-left: 13px;
  overflow: hidden;
}
.song-title {
  font-size: 14px;
  font-weight: 600;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
.artist {
  color: #777;
  font-size: 12px;
  margin-top: 5px;
}
.song-number {
  color: #b89038;
  font-size: 13px;
  margin-right: 8px;
}
/* PLAYER */
.player {
  position: fixed;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(8,8,8,.96);
  backdrop-filter: blur(20px);
  border-top: 1px solid #332711;
  padding: 12px 18px calc(12px + env(safe-area-inset-bottom));
  z-index: 20;
}
.player-inner {
  max-width: 600px;
  margin: auto;
}
.now {
  display: flex;
  align-items: center;
  gap: 12px;
}
.now img {
  width: 48px;
  height: 48px;
  border-radius: 10px;
  object-fit: cover;
}
.now-info {
  flex: 1;
  min-width: 0;
}
.now-title {
  font-weight: 700;
  font-size: 14px;
}
.now-artist {
  color: #777;
  font-size: 11px;
  margin-top: 3px;
}
.play-btn {
  width: 47px;
  height: 47px;
  border-radius: 50%;
  border: none;
  background: linear-gradient(145deg, #e1bd62, #9b7223);
  color: #080808;
  font-size: 19px;
  font-weight: bold;
  box-shadow: 0 0 18px rgba(214,173,75,.18);
}
.progress {
  width: 100%;
  height: 4px;
  margin-top: 12px;
  appearance: none;
  background: #292929;
  border-radius: 10px;
}
.progress::-webkit-slider-thumb {
  appearance: none;
  width: 11px;
  height: 11px;
  background: #d6ad4b;
  border-radius: 50%;
}
.time {
  display: flex;
  justify-content: space-between;
  color: #666;
  font-size: 9px;
  margin-top: 4px;
}
.empty {
  text-align: center;
  color: #666;
  padding: 30px 0;
}
</style>
</head>
<body>
<div class="app">
  <div class="header">
    <div class="logo">GOLD<span class="gold">MUSIC</span></div>
    <div class="profile">♪</div>
  </div>
  <input
    id="search"
    class="search"
    type="text"
    placeholder="🔎  Qo‘shiq yoki ijrochi qidirish..."
  >
  <div class="section-title">
    Playlistlar
    <div class="subtitle">Siz uchun tanlangan musiqa</div>
  </div>
  <div class="playlists">
    <div class="playlist">
      <img src="https://images.unsplash.com/photo-1519608487953-e999c86e7455?auto=format&fit=crop&w=500&q=80">
      <div class="playlist-name">
        Night
        <span>Vibes</span>
      </div>
    </div>
    <div class="playlist">
      <img src="https://images.unsplash.com/photo-1470229722913-7c0e2dbbafd3?auto=format&fit=crop&w=500&q=80">
      <div class="playlist-name">
        Energy
        <span>Mix</span>
      </div>
    </div>
    <div class="playlist">
      <img src="https://images.unsplash.com/photo-1493225457124-a3eb161ffa5f?auto=format&fit=crop&w=500&q=80">
      <div class="playlist-name">
        Chill
        <span>Session</span>
      </div>
    </div>
  </div>
  <div class="section-title">Qo‘shiqlar</div>
  <div id="songs" class="songs"></div>
</div>
<div class="player">
  <div class="player-inner">
    <div class="now">
      <img id="nowCover"
           src="https://images.unsplash.com/photo-1519608487953-e999c86e7455?auto=format&fit=crop&w=300&q=80">
      <div class="now-info">
        <div id="nowTitle" class="now-title">Qo‘shiq tanlang</div>
        <div id="nowArtist" class="now-artist">GOLD MUSIC</div>
      </div>
      <button id="playBtn" class="play-btn">▶</button>
    </div>
    <input id="progress"
           class="progress"
           type="range"
           min="0"
           max="100"
           value="0">
    <div class="time">
      <span id="currentTime">0:00</span>
      <span id="duration">0:00</span>
    </div>
  </div>
</div>
<audio id="audio"></audio>
<script>
const tg = window.Telegram?.WebApp;
if (tg) {
  tg.ready();
  tg.expand();
}
/* SONGS */
const songs = [
  {
    title: "Night Drive",
    artist: "SoundHelix",
    cover: "https://images.unsplash.com/photo-1519608487953-e999c86e7455?auto=format&fit=crop&w=500&q=80",
    audio: "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3"
  },
  {
    title: "Golden Night",
    artist: "SoundHelix",
    cover: "https://images.unsplash.com/photo-1470229722913-7c0e2dbbafd3?auto=format&fit=crop&w=500&q=80",
    audio: "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-2.mp3"
  },
  {
    title: "Midnight",
    artist: "SoundHelix",
    cover: "https://images.unsplash.com/photo-1493225457124-a3eb161ffa5f?auto=format&fit=crop&w=500&q=80",
    audio: "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-3.mp3"
  }
];
const songsBox = document.getElementById("songs");
const audio = document.getElementById("audio");
const nowTitle = document.getElementById("nowTitle");
const nowArtist = document.getElementById("nowArtist");
const nowCover = document.getElementById("nowCover");
const playBtn = document.getElementById("playBtn");
const progress = document.getElementById("progress");
const currentTime = document.getElementById("currentTime");
const duration = document.getElementById("duration");
const search = document.getElementById("search");
let current = -1;
/* RENDER */
function render(list = songs) {
  songsBox.innerHTML = "";
  if (!list.length) {
    songsBox.innerHTML =
      '<div class="empty">Hech narsa topilmadi</div>';
    return;
  }
  list.forEach((song, index) => {
    const realIndex = songs.indexOf(song);
    const div = document.createElement("div");
    div.className =
      "song " + (realIndex === current ? "active" : "");
    div.innerHTML = `
      <img class="cover" src="${song.cover}">
      <div class="song-info">
        <div class="song-title">${song.title}</div>
        <div class="artist">${song.artist}</div>
      </div>
      <div class="song-number">${realIndex === current ? "●" : "▶"}</div>
    `;
    div.onclick = () => playSong(realIndex);
    songsBox.appendChild(div);
  });
}
render();
/* PLAY */
function playSong(index) {
  current = index;
  const song = songs[index];
  audio.src = song.audio;
  nowTitle.textContent = song.title;
  nowArtist.textContent = song.artist;
  nowCover.src = song.cover;
  audio.play()
    .then(() => {
      playBtn.textContent = "Ⅱ";
    })
    .catch(() => {
      playBtn.textContent = "▶";
    });
  render(
    songs.filter(s =>
      s.title.toLowerCase().includes(search.value.toLowerCase()) ||
      s.artist.toLowerCase().includes(search.value.toLowerCase())
    )
  );
}
/* PLAY / PAUSE */
playBtn.onclick = () => {
  if (current === -1) {
    playSong(0);
    return;
  }
  if (audio.paused) {
    audio.play();
    playBtn.textContent = "Ⅱ";
  } else {
    audio.pause();
    playBtn.textContent = "▶";
  }
};
/* PROGRESS */
audio.addEventListener("loadedmetadata", () => {
  duration.textContent =
    formatTime(audio.duration);
});
audio.addEventListener("timeupdate", () => {
  if (!audio.duration) return;
  progress.value =
    (audio.currentTime / audio.duration) * 100;
  currentTime.textContent =
    formatTime(audio.currentTime);
});
progress.oninput = () => {
  if (!audio.duration) return;
  audio.currentTime =
    (progress.value / 100) * audio.duration;
};
/* NEXT SONG */
audio.addEventListener("ended", () => {
  if (current < songs.length - 1) {
    playSong(current + 1);
  } else {
    playBtn.textContent = "▶";
  }
});
/* SEARCH */
search.addEventListener("input", () => {
  const text =
    search.value.toLowerCase();
  const filtered = songs.filter(song =>
    song.title.toLowerCase().includes(text) ||
    song.artist.toLowerCase().includes(text)
  );
  render(filtered);
});
function formatTime(seconds) {
  if (!seconds || isNaN(seconds))
    return "0:00";
  const min =
    Math.floor(seconds / 60);
  const sec =
    Math.floor(seconds % 60)
      .toString()
      .padStart(2, "0");
  return `${min}:${sec}`;
}
</script>
</body>
</html>
