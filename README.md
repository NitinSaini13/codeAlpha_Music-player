# codeAlpha_Music-Sytem
#Task-3
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>#Task-3 || Music Player</title>
    <link rel="stylesheet" href="style.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/css/all.min.css" integrity="sha512-SnH5WK+bZxgPHs44uWIX+LLJAJ9/2PkPKZ5QiAj6Ta86w+fsb2TkcmfRyVX3pBnMFcV7oQPJkl9QevSCWr3W6A==" crossorigin="anonymous" referrerpolicy="no-referrer" />
</head>
<body>
    <div class="container">
        <div class="music-player">
<nav>
    <div class="circle">
        <i class="fa-solid fa-angle-left"></i>
    </div>
    <div class="circle">
        <i class="fa-solid fa-bars"></i>
    </div>
</nav>
<img src="media/img.jpeg" class="song-img">
<h1>Mi Amor</h1>
<p>Sharn Jhutty and The Paul</p>
<audio controls id="song">
    <source src="media/MI Amor.mp3" type="audio/mpeg">
</audio>
<input type="range" value="0" id="progress">

<div class="controls">
    <div><i class="fa-solid fa-backward"></i></div>
    <div onclick="playPause()"><i class="fa-solid fa-play" id="ctrlIcon"></i></div>
    <div><i class="fa-solid fa-forward"></i></div>
</div>
        </div>
    </div>

    <script>
        let progress=document.getElementById("progress");
        let song=document.getElementById("song");
        let ctrlIcon=document.getElementById("ctrlIcon");

        song.onloadedmetadata=function(){
            progress.max=song.duration;
            progress.value=song.currentTime;
        }
        function playPause(){
            if(ctrlIcon.classList.contains("fa-pause")){
                song.pause();
                ctrlIcon.classList.remove("fa-pause");
                ctrlIcon.classList.add("fa-play");
            }
            else{
                song.play();
                ctrlIcon.classList.add("fa-pause");
                ctrlIcon.classList.remove("fa-play");
            }
        }
        if(song.play()){
            setInterval(()=>{
                progress.value=song.currentTime;
            },500);
        }
        progress.onchange=function(){
            song.play();
            song.currentTime=progress.value;
            ctrlIcon.classList.add("fa-pause");
            ctrlIcon.classList.remove("fa-play");
        }

    </script>
</body>
</html>
style.css
*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family:'Times New Roman', Times, serif;
}
.container{
    width:100%;
    height: 100vh;
    background: #333;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-wrap: wrap;


}
.music-player{
    background: #c5ebeb;
    width: 480px;
    padding: 25px 35px;
    text-align:center;
}
nav{
    display: flex;
    justify-content: space-between;
    margin-bottom: 30px;
}
nav .circle{
    border-radius: 50%;
    width: 40px;
    height: 40px;
    line-height: 40px;
    background-color:white;
    color: #37cfd7;
    box-shadow: 0 5px 10px  #c5ebeb;
    cursor: pointer;
}
.song-img{
    width: 220px;
    border-radius: 50%;
    border: 8px solid white;
    box-shadow: 0 10px 60px  #c5ebeb;
    cursor: pointer;
}
.music-player h1{
   font-size: 20px;
   color:rgb(63, 62, 62);
   margin-top:20px; 
}
.music-player p{
    font-size: 14px;
    color:rgb(63, 62, 62);
}
#progress{
    -webkit-appearance: none;
    width: 100%;
    height: 6px;
    background: #37cfd7;;
    border-radius: 4px;
    cursor: pointer;
    margin: 40px 0;
}
#progress::-webkit-slider-track{
    -webkit-appearance: none;
    background: #37cfd7;;
    width: 30px;
    height: 30px;
    border-radius: 50%;
   border: 8px solid white;
    box-shadow: 0 5px 5px  #c5ebeb;
}
.controls{
    display: flex;
    justify-content: center;
    align-items: center;
}
.controls div{
    width: 60px;
    height: 60px;
    margin: 20px;
    background: #fff;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    border-radius: 50%;
    color:#37cfd7;
    box-shadow: 0 5px 5px  #c5ebeb;
      cursor: pointer;
}
.controls div:nth-child(2){
    transform: scale(1.5);
    background: #37cfd7;;
    color: #fff;
}
