<!DOCTYPE html>
<html lang="uz">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">

<title>GOLD MUSIC</title>

<script src="https://telegram.org/js/telegram-web-app.js"></script>

<style>
*{
    box-sizing:border-box;
    margin:0;
    padding:0;
}

body{
    background:#050505;
    color:#fff;
    font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif;
    min-height:100vh;
    padding-bottom:135px;
}

.app{
    width:100%;
    max-width:650px;
    margin:auto;
    padding:22px 18px;
}

/* HEADER */

.header{
    display:flex;
    align-items:center;
    justify-content:space-between;
    margin-bottom:25px;
}

.logo{
    font-size:23px;
    font-weight:800;
    letter-spacing:3px;
}

.logo span{
    color:#d4af37;
}

.menu{
    width:42px;
    height:42px;
    border:1px solid #4d3b16;
    border-radius:50%;
    display:flex;
    align-items:center;
    justify-content:center;
    color:#d4af37;
    font-size:20px;
}

/* HERO */

.hero{
    background:
      radial-gradient(circle at 80% 20%,rgba(212,175,55,.20),transparent 35%),
      linear-gradient(145deg,#17130a,#080808 65%);
    border:1px solid #332811;
    border-radius:24px;
    padding:25px 22px;
    margin-bottom:25px;
}

.hero small{
    color:#9b8241;
    letter-spacing:2px;
    font-size:11px;
}

.hero h1{
    font-size:30px;
    margin-top:8px;
    letter-spacing:-1px;
}

.hero p{
    color:#777;
    font-size:13px;
    margin-top:7px;
}

/* SEARCH */

.search{
    width:100%;
    height:52px;
    background:#101010;
    border:1px solid #242424;
    border-radius:16px;
    outline:none;
    color:white;
    padding:0 17px;
    font-size:14px;
    margin-bottom:27px;
}

.search:focus{
    border-color:#a68735;
}

.search::placeholder{
    color:#666;
}

/* SECTION */

.section{
    display:flex;
    align-items:center;
    justify-content:space-between;
    margin-bottom:14px;
}

.section h2{
    font-size:18px;
}

.section span{
    color:#9a8040;
    font-size:11px;
}

/* PLAYLIST */

.playlists{
    display:flex;
    gap:14px;
    overflow-x:auto;
    padding-bottom:7px;
    margin-bottom:30px;
}

.playlists::-webkit-scrollbar{
    display:none;
}

.playlist{
    position:relative;
    min-width:145px;
    height:165px;
    border-radius:19px;
    overflow:hidden;
    border:1px solid #2b2413;
}

.playlist img{
    width:100%;
    height:100%;
    object-fit:cover;
}

.playlist:after{
    content:"";
    position:absolute;
    inset:0;
    background:linear-gradient(
        transparent 25%,
        rgba(0,0,0,.95)
    );
}

.playlistText{
    position:absolute;
    z-index:2;
    left:13px;
    bottom:13px;
}

.playlistText b{
    font-size:15px;
}

.playlistText small{
    display:block;
    color:#d4af37;
    margin-top:4px;
    font-size:10px;
}

/* SONG */

.song{
    display:flex;
    align-items:center;
    padding:9px;
    margin-bottom:9px;
    background:#0d0d0d;
    border:1px solid #181818;
    border-radius:16px;
    transition:.2s;
}

.song:active{
    transform:scale(.98);
}

.song.active{
    background:#151208;
    border-color:#806526;
}

.cover{
    width:55px;
    height:55px;
    border-radius:12px;
    object-fit:cover;
}

.songInfo{
    flex:1;
    min-width:0;
    margin-left:13px;
}

.songTitle{
    font-size:14px;
    font-weight:600;
    white-space:nowrap;
    overflow:hidden;
    text-overflow:ellipsis;
}

.artist{
    color:#707070;
    font-size:12px;
    margin-top:5px;
}

.songPlay{
    width:38px;
    height:38px;
    border-radius:50%;
    border:1px solid #59471e;
    color:#d4af37;
    display:flex;
    align-items:center;
    justify-content:center;
    margin-left:8px;
}

/* PLAYER */

.player{
    position:fixed;
    z-index:100;
    left:0;
    right:0;
    bottom:0;
    padding:12px 17px calc(12px + env(safe-area-inset-bottom));
    background:rgba(7,7,7,.96);
    backdrop-filter:blur(22px);
    border-top:1px solid #302611;
}

.playerInside{
    max-width:650px;
    margin:auto;
}

.playerTop{
    display:flex;
    align-items:center;
}

.playerCover{
    width:50px;
    height:50px;
    border-radius:11px;
    object-fit:cover;
}

.playerInfo{
    flex:1;
    min-width:0;
    margin-left:12px;
}

.playerTitle{
    font-size:14px;
    font-weight:700;
    white-space:nowrap;
    overflow:hidden;
    text-overflow:ellipsis;
}

.playerArtist{
    color:#707070;
    font-size:11px;
    margin-top:4px;
}

.playButton{
    width:47px;
    height:47px;
    border-radius:50%;
    border:none;
    background:linear-gradient(145deg,#e7ca6d,#a77e20);
    color:#080808;
    font-size:18px;
    font-weight:bold;
}

.progress{
    width:100%;
    height:4px;
    margin-top:11px;
    appearance:none;
    background:#292929;
    border-radius:5px;
}

.progress::-webkit-slider-thumb{
    appearance:none;
    width:11px;
    height:11px;
    border-radius:50%;
    background:#d4af37;
}

.times{
    display:flex;
    justify-content:space-between;
    color:#555;
    font-size:9px;
    margin-top:4px;
}

/* EMPTY */

.empty{
    text-align:center;
    padding:35px 0;
    color:#666;
}
</style>
</head>

<body>

<div class="app">

    <div class="header">
        <div class="logo">
            GOLD<span>MUSIC</span>
        </div>

        <div class="menu">♪</div>
    </div>


    <div class="hero">
        <small>PREMIUM MUSIC</small>
        <h1>Music for your mood.</h1>
        <p>Sevimli qo‘shiqlaringizni bir joyda tinglang.</p>
    </div>


    <input
        id="search"
        class="search"
        type="text"
        placeholder="🔎  Qo‘shiq yoki ijrochi qidirish..."
    >


    <div class="section">
        <h2>Playlistlar</h2>
        <span>EXPLORE</span>
    </div>


    <div class="playlists">

        <div class="playlist">
            <img src="https://images.unsplash.com/photo-1519608487953-e999c86e7455?auto=format&fit=crop&w=500&q=80">

            <div class="playlistText">
                <b>Night Vibes</b>
                <small>12 TRACKS</small>
            </div>
        </div>


        <div class="playlist">
            <img src="https://images.unsplash.com/photo-1470229722913-7c0e2dbbafd3?auto=format&fit=crop&w=500&q=80">

            <div class="playlistText">
                <b>Energy</b>
                <small>18 TRACKS</small>
            </div>
        </div>


        <div class="playlist">
            <img src="https://images.unsplash.com/photo-1493225457124-a3eb161ffa5f?auto=format&fit=crop&w=500&q=80">

            <div class="playlistText">
                <b>Chill</b>
                <small>15 TRACKS</small>
            </div>
        </div>

    </div>


    <div class="section">
        <h2>Qo‘shiqlar</h2>
        <span id="count">3 TRACKS</span>
    </div>


    <div id="songs"></div>

</div>


<div class="player">

    <div class="playerInside">

        <div class="playerTop">

            <img
                id="playerCover"
                class="playerCover"
                src="https://images.unsplash.com/photo-1519608487953-e999c86e7455?auto=format&fit=crop&w=300&q=80"
            >

            <div class="playerInfo">

                <div id="playerTitle" class="playerTitle">
                    Qo‘shiq tanlang
                </div>

                <div id="playerArtist" class="playerArtist">
                    GOLD MUSIC
                </div>

            </div>

            <button id="playButton" class="playButton">
                ▶
            </button>

        </div>


        <input
            id="progress"
            class="progress"
            type="range"
            min="0"
            max="100"
            value="0"
        >


        <div class="times">
            <span id="currentTime">0:00</span>
            <span id="duration">0:00</span>
        </div>

    </div>

</div>


<audio id="audio"></audio>


<script>

const tg = window.Telegram?.WebApp;

if(tg){
    tg.ready();
    tg.expand();
}


/* MUSIC */

const songs = [

    {
        title:"Night Drive",
        artist:"SoundHelix",
        cover:"https://images.unsplash.com/photo-1519608487953-e999c86e7455?auto=format&fit=crop&w=500&q=80",
        audio:"https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3"
    },

    {
        title:"Golden Night",
        artist:"SoundHelix",
        cover:"https://images.unsplash.com/photo-1470229722913-7c0e2dbbafd3?auto=format&fit=crop&w=500&q=80",
        audio:"https://www.soundhelix.com/examples/mp3/SoundHelix-Song-2.mp3"
    },

    {
        title:"Midnight",
        artist:"SoundHelix",
        cover:"https://images.unsplash.com/photo-1493225457124-a3eb161ffa5f?auto=format&fit=crop&w=500&q=80",
        audio:"https://www.soundhelix.com/examples/mp3/SoundHelix-Song-3.mp3"
    }

];


const songsBox=document.getElementById("songs");
const audio=document.getElementById("audio");

const search=document.getElementById("search");
const count=document.getElementById("count");

const playerCover=document.getElementById("playerCover");
const playerTitle=document.getElementById("playerTitle");
const playerArtist=document.getElementById("playerArtist");

const playButton=document.getElementById("playButton");

const progress=document.getElementById("progress");

const currentTime=document.getElementById("currentTime");
const duration=document.getElementById("duration");

let current=-1;


/* RENDER */

function render(list=songs){

    songsBox.innerHTML="";

    count.textContent=list.length+" TRACKS";

    if(list.length===0){

        songsBox.innerHTML=
        '<div class="empty">Hech narsa topilmadi</div>';

        return;
    }


    list.forEach(song=>{

        const index=songs.indexOf(song);

        const div=document.createElement("div");

        div.className=
        "song "+(index===current?"active":"");


        div.innerHTML=`

            <img
                class="cover"
                src="${song.cover}"
            >

            <div class="songInfo">

                <div class="songTitle">
                    ${song.title}
                </div>

                <div class="artist">
                    ${song.artist}
                </div>

            </div>

            <div class="songPlay">
                ${index===current && !audio.paused ? "Ⅱ":"▶"}
            </div>
        `;


        div.onclick=()=>playSong(index);

        songsBox.appendChild(div);

    });

}


render();


/* PLAY */

function playSong(index){

    current=index;

    const song=songs[index];

    audio.src=song.audio;

    playerTitle.textContent=song.title;
    playerArtist.textContent=song.artist;

    playerCover.src=song.cover;

    audio.play()
    .then(()=>{

        playButton.textContent="Ⅱ";

        render();

    })
    .catch(()=>{

        playButton.textContent="▶";

    });

}


/* PLAY BUTTON */

playButton.onclick=()=>{

    if(current===-1){

        playSong(0);

        return;
    }


    if(audio.paused){

        audio.play();

        playButton.textContent="Ⅱ";

    }else{

        audio.pause();

        playButton.textContent="▶";

    }

    render();

};


/* PROGRESS */

audio.addEventListener("loadedmetadata",()=>{

    duration.textContent=
    formatTime(audio.duration);

});


audio.addEventListener("timeupdate",()=>{

    if(!audio.duration)return;

    progress.value=
    (audio.currentTime/audio.duration)*100;

    currentTime.textContent=
    formatTime(audio.currentTime);

});


progress.addEventListener("input",()=>{

    if(!audio.duration)return;

    audio.currentTime=
    (progress.value/100)*audio.duration;

});


/* NEXT */

audio.addEventListener("ended",()=>{

    if(current<songs.length-1){

        playSong(current+1);

    }else{

        playButton.textContent="▶";

        render();

    }

});


/* SEARCH */

search.addEventListener("input",()=>{

    const text=
    search.value.toLowerCase();

    const filtered=songs.filter(song=>

        song.title.toLowerCase().includes(text) ||

        song.artist.toLowerCase().includes(text)

    );

    render(filtered);

});


/* TIME */

function formatTime(seconds){

    if(!seconds || isNaN(seconds))
        return "0:00";

    const minutes=
    Math.floor(seconds/60);

    const secondsPart=
    Math.floor(seconds%60)
    .toString()
    .padStart(2,"0");

    return minutes+":"+secondsPart;

}

</script>

</body>
</html>
