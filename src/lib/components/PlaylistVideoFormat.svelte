<script>
    import deo from "$lib/video/1.mp4";
    import imgs from "$lib/images/IDENTITE.jpeg";
    import Fa from "svelte-fa";
    import {  faPlay,faEye  } from '@fortawesome/free-solid-svg-icons';
    export let videoUrl;
    let duration;

    function timerConvert(dure){
         
        if(isNaN(dure)) return '...';
        const minutes = Math.floor(dure / 60);
        dure = Math.floor(dure % 60);
        if(dure < 10) dure ='0' + dure;
        return `${minutes}:${dure}`;
    }

</script>

<div class="main">
    <div class="container">
        <div class="video">
            <video
                width="130"
                height="90"
                src="{videoUrl}"
                bind:duration={duration}>
                <track kind="captions"/>
            </video>
            <span class="time">{timerConvert(duration)}</span>
            <span class="play">
                <Fa icon={faPlay} size="0.5x"></Fa>
            </span>
        </div>
        <div class="video-info">
            <span class="title">JESUS[THE NEW CHAPTER]</span>
            <div class="body">
                <img width="20" height="20" src="{imgs}" alt="">
                <span class="channel-name">Gracias_Jr</span>
            </div>
            <span class="vues">
                <Fa icon={faEye}></Fa>
                150k vues
            </span>
        </div>
    </div>
</div>


<style>

    .main{
        padding-top: 10px;
        width: auto;
    }

    .container{
        /* border: 1px solid; */
        width: 100%;
        height: 100px;
        display: flex;
        justify-content: start;
        align-items: center;
        gap:3px;
    }

    .video{
        position: relative;
    }
    
    .video video{
        object-fit: cover;
        object-position: top;
        border-radius: 7px;
        cursor: pointer;
        transition: 0.3s ease-out;
        background: #ffffff23;
    }

    .video:hover::before{
        content: "";
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 95%;
        background: #ffffff23;
        border-radius: 7px;
    }

    .video .time{
        position: absolute;
        font-size: 10px;
        top: 10px;
        left: 5px;
        padding: 5px;
        background: #333333c2/*ffffff23*/;
        border-radius: 5px;
    }

    .video .play{
        position: absolute;
        bottom:10px;
        right: 5px;
        display: flex;
        align-items: center;
        justify-content: center;
        padding:5px 7px;
        background: #333333c2/*ffffff23*/;
        border-radius: 5px;
        cursor: pointer;
    }
    .video-info{
        /* border: 1px solid; */
        width: 75%;
        height: 95%;
        display: flex;
        padding:7px;
        flex-direction: column;
        overflow: hidden;
        justify-content: space-between;
        gap: 10px;
    }

    .video-info .title{
        font-size: 12px;
        font-weight: bold;
        white-space: nowrap;
        overflow-x: hidden;
        text-overflow: ellipsis;

    }

    .body{
        display: flex;
        align-items: center;
        gap: 5px;
    }

    .body .channel-name{
        font-size: 10px;
        color: #ffffffce;
    }

    .video-info img{
        border-radius: 15%;
    }
    .vues{
        font-size: 10px;
        color: #ffffffce;        
    }
</style>