<script>
    // import Video from '$lib/video/1.mp4';
    import Photo from '$lib/images/IDENTITE.jpeg'
    import Fa from 'svelte-fa';
    import { faPlay,faPause,faVolumeMute,faVolumeHigh,faExpand,faThumbsUp,faThumbsDown,faShareNodes,faFileArrowDown,faArrowsDownToLine,faEllipsis} from '@fortawesome/free-solid-svg-icons'
    import { page } from '$app/stores';

    let time =0;
    let duration;
    let paused = true;
    $:showCommandes = false;
    let muted = false
    let vol;

    // videoSrc : temporaire
    let videoSrc =""
    $:slug = $page.params.slug;
    $:showAddPlaylist = false;
    $:adding=false;
    
    $:plus=false;
    
    


    function progress(e){
        setTimeout(() => { showCommandes=false}, 10000);
        showCommandes=true;
        const {left,right} = this.getBoundingClientRect();
        const clientX = e.type === "touchemove" ? e.touches[0].clientX:e.clientX;
    }

    function Play(e){
        if(paused){
            paused =!paused            
        }else{
            paused =!paused            
        }       
    }

    function timer(seconds){
        if(isNaN(seconds)) return '...';
        const minutes = Math.floor(seconds / 60);
        seconds = Math.floor(seconds % 60);
        if(seconds < 10) seconds ='0' + seconds;
        return `${minutes}:${seconds}`;
    }
    
    function fullscreen(e){        
         this.requestFullscreen();
    }

    function addToPlayList(){

    }

</script>
  
<section>
    <header>
        <div class="video-container">
            <video src="{videoSrc}"
                style="cursor:{showCommandes?'auto':'none'};"
                on:click={Play}
                on:mousemove={progress}
                on:touchmove|preventDefault={progress}
                bind:currentTime={time}
                bind:duration={duration}
                bind:paused={paused}
                bind:muted={muted}
                bind:volume={vol}
                on:dblclick={fullscreen}
                
                 >
                <track kind="captions"/>
            </video>
            <progress style="opacity: {showCommandes?1:0};" value="{(time / duration) || 0}" on:touchmove|preventDefault={progress} />
            <div class="top-panel" style="opacity: {showCommandes?1:0};">
                <span class="current-time">{timer(time)}</span>
                <span class="duration">{timer(duration)}</span>
            </div>
            <div class="video-command" style="opacity: {showCommandes?1:0};">
                <div class="left-panel">
                    <div class="btn">            
                        <button class="command" id="play-pause" on:click={Play} style="cursor:{showCommandes?'pointer':''}">
                            {#if paused}
                                <Fa icon={faPlay} size="1x" ></Fa>
                            {:else}                            
                                <Fa icon={faPause} size="1x" ></Fa>
                            {/if}
                        </button>
                        <span>
                            {#if paused}
                                play
                            {:else}
                                pause
                            {/if}
                        </span>
                    </div>
                    <div class="btn">
                        <button class="command" id="volume" on:click={()=>{muted=!muted}} style="cursor:{showCommandes?"pointer":""};">
                            {#if !muted}
                                <Fa icon={faVolumeHigh} size="1x"></Fa>   
                            {:else}                         
                                <Fa icon={faVolumeMute} size="1x"></Fa>
                            {/if}
                        </button>
                        <span>Volume</span>   
                    </div> 
                </div>                
                <div class="btn">
                    <button class="command" id="full-screen" style="cursor:{showCommandes?"pointer":''}">
                        <Fa icon={faExpand} size="1x"></Fa>
                    </button>
                    <span class="full-scr">Full Screen</span>
                </div>
            </div>
        </div>
        <div class="header-footer">
            <div class="hf-left-panel">
                <h2 class="video-title">
                    JESUS [THE NEW CHAPTER]
                </h2>
                <span class="video-view">
                    150k vues
                </span>
            </div>
            <div class="hf-right-panel">
                <div class="hf-btn ThumbsUp">
                    <button>
                        <Fa icon={faThumbsUp}></Fa>
                    </button>
                </div>
                <div class="hf-btn ThumbsDown">
                    <button>
                        <Fa icon={faThumbsDown}></Fa>
                    </button>
                    <span>DISLIKE</span>
                </div>              
                <div class="hf-btn">
                    <a href="https://youtube.com/{slug}">
                        <button>
                            <Fa icon={faFileArrowDown}></Fa>
                        </button>
                        <span>SAVE</span>
                    </a>
                </div>
                <div class="hf-btn">
                    <button>
                        <Fa icon={faShareNodes}></Fa>
                    </button>
                    <span>SHARE</span>
                </div>
                <div class="hf-btn">
                    <button on:click={()=>{showAddPlaylist=!showAddPlaylist}}>
                        <Fa icon={faEllipsis}></Fa>
                    </button>
                    {#if showAddPlaylist }                        
                        <div class="more-options">
                            <button on:click={()=>{adding=!adding;showAddPlaylist=!showAddPlaylist}}>
                                Add to PlayList
                            </button>
                        </div>
                    {/if}
                </div>
            </div>
        </div>
    </header>

    <div class="description">
        <div class="profile">
            <img width="50" height="50" src="{Photo}" alt="">
            <span class="profile-name">
                Gracias_Jr
            </span>
        </div>
        <div class="descrpt-contain">
           <span class="descrpt" style="white-space:{plus?'':'nowrap'};transition:white-space 0.5s ease-out;">
                Lorem ipsum dolor sit amet consectetur adipisicing elit. Repellat maiores asperiores delectus! Autem tempore voluptas nam ab porro dolor non, eaque accusamus expedita, quaerat inventore aperiam magnam velit sequi laboriosam.
                Esse aspernatur eius velit ea cupiditate quasi cum libero repellendus odio veritatis nobis, eum dolores! Nesciunt a sint ab delectus facere maxime unde officiis ullam? Veniam animi architecto omnis totam.
            </span>
            <button class="plusMoins" on:click={()=>{plus=!plus}} >
                {#if !plus}
                    <span>Plus</span>
                {:else}
                    <span>Moins</span>
                {/if}
            </button>
        </div>
    </div>

    {#if adding}
        <div class="playlistChooser">
            <h3>Playlists</h3>
            <div class="list">
                <span class="name">Tribl</span>
                <button on:click={()=>{adding=!adding}}>Add</button>
            </div>
        </div>
    {/if}



</section>

<style>

    section{
        display: flex;
        flex-direction: column;
        padding: 0;
    }

    header{
        display: flex;
        flex-direction: column;
        gap: 10px;
    }

    .video-container{
        width:95%;
        margin-top:1%;
        margin-left: 2%;
        height: 70vh;
        position: relative;
    }

    video{
        width: 100%;
        height: 100%;
        position: absolute;
        object-fit: cover;
        object-position: top;
        top: 0;
        border-radius: 7px;
    }

    .video-command{
        /* border: 1px solid green; */
        position: absolute;
        bottom: 0;
        width: 100%;
        height: 9vh;
        padding:0 5px; 
        display: flex;
        align-items: center;
        justify-content: space-between;
        background:#ffffff23;
        backdrop-filter: blur(15px);
        -webkit-backdrop-filter: blur(15px);
        border-bottom-left-radius: 7px;
        border-bottom-right-radius: 7px;
        transition: opacity 1.5s ease-out;
        z-index: 1;
    }

    .btn span{
        /* border: 1px solid; */
        position: absolute;
        width: auto;
        font-size: 12px;
        background: #000;
        padding: 4px 7px;
        border-radius: 3px;
        color: #cfcbcb;
        top: -23px;
        display: none;
        z-index:999;

    }

    .btn span.full-scr{
        right:5px;
    }

    .btn:hover span{
        display: block;
    }

    button.command{
        border:0px;
        width:25px;
        height:25px;
        border-radius: none;
        background: transparent;
        display: flex;
        align-items: center;
        justify-content: center; 
        color: #e2e0e0;
        /* cursor: pointer; */
        transition:all 0.3s ease-out;
    }


    .top-panel{
        /* border: 1px solid crimson; */
        position: absolute;
        width: 100%;
        height: auto;
        bottom:9.5vh;
        display: flex;
        justify-content: space-between;
        padding: 0 5px;
        font-size: 10px;
        /* z-index: 2; */
    }

    .left-panel{
        /* border: 1px solid; */
        display: flex;
        gap: 12px;
    }

    progress{
        width: 100%;
        height:2px;
        position: absolute;
        bottom:9vh;
        appearance: none;
        cursor: pointer;
        background: royalblue;
    }

    progress,
    .top-panel,
    .video-command{
        transition: opacity 0.3s ease-out;
    }

    progress::-webkit-progress-value{
        background:linear-gradient(#fff,#ccc);
    }

    .header-footer{
        border-bottom: 1px solid #ffffff23;
        width: 100%;
        height: 10vh;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0 2%;
    }

    .hf-left-panel{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: start;
        gap: 3px;
    }

    .hf-left-panel h2{
        width: 100%;
        color:#e0dede ;
    }

    .video-view{
        width: auto;
        color: #a3a0a0;
        font-size: 13px;
    }

    .hf-left-panel,
    .hf-right-panel{
        width: 50%;
    }

    .hf-right-panel{
        height: 100%;
        display: flex;
        justify-content: space-between;        
        align-items:center;
        
    }

    .hf-btn{
        position: relative;
        width: auto;
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 3px;
        padding: 5px 10px;
        border-radius: 50px;
        font-size: 13px;
        background-color: #ffffff10;
        cursor: pointer;
        transition:all 0.3s ease-out;
    }

    .hf-btn a{
        text-decoration: none;
        color: inherit;
    }

    .hf-btn:hover{
        background-color: #ffffff27;
    }

    .hf-btn button{
        border:0px;
        width: 24px;
        height: 24px;
        background: transparent;
        color: #ffff;
        cursor: pointer;

    }

    .more-options{
        border: 1px solid;
        position: absolute;
        display:flex;
        width:auto;
        height: auto;
        left:-90px;
        bottom: 40px;
        font-size: 10px;
        z-index: 3;
    }
    
    .more-options button{
        border: 0px;
        width: auto;
        font-weight: bold;
        padding:5px 5px 5px 5px;
        transition: all ease-out;
    }

    .more-options button:hover{
        color:#000;
        background-color: #fff;
    }

    .playlistChooser{
        border: 2px solid #fff;
        border-radius: 7px;
        position: absolute;
        width: 250px;
        display: flex;
        flex-direction: column;
        padding: 10px;
        font-size: 15px;
        top: 30%;
        left: 30%;
        gap:5px;
        background:var(--color1);
    }

    .playlistChooser h3{
        display: inline-block;
        margin: 0 auto;
        text-decoration: underline;
        margin-bottom: 7px;
    }
    .playlistChooser .list{
        /* border: 1px solid; */
        width:100%;
        height: 7vh;
		display: flex;
		position: relative;
		align-items: center;
        border-radius: 50px;
		background:var(--color5);
        font-weight: bold;
    }

    .list .name{
        width:70%;
        padding: 7px 0;
        text-align: center;
    }

    .list button{
        border: 0px;
        width:30%;
        height: 100%;
        font-weight: bold;
        border-radius:0 50px 50px 0px;
        background-color: #ffffff27;
        color: #fff;
        cursor: pointer;
    }

    .list button:hover{
        background:#ffffff41 ;
    }

    
    .ThumbsUp,
    .ThumbsDown,
    .ThumbsUp button,
    .ThumbsDown button{        
        cursor: no-drop;
    }

    .description{
        border: 1px solid;
        width: 100%;
        padding-top:2%;
        display: flex;
        flex-direction: column;
        align-items: start;
    }

    .profile{
        width: auto;
        margin-left: 2%;
        margin-bottom: 1%;
        display: flex;
        align-items: center;
        justify-content: start;
        gap: 5px;
    }
    
    .profile img{
        object-fit: cover;
        object-position: top;
        border-radius: 50%;
    }

    .profile span{
        font-weight: bold;
    }

    .descrpt-contain{
        /* border: 1px solid green;  */
        width: 97%;
        height: auto;
        margin-bottom: 5px;
        padding: 0 0 0 1.5%;
        display: flex;
        flex-direction: column;
        align-items: end;
        position: relative;
        margin-bottom: 3px;
        font-size: 12px;
    }

    .descrpt{
        /* border: 1px solid #dddddd27; */
        border-radius: 0 0 10px 0;
        padding: 1% 0 1% 2%;
        display: block;
        width: 100%;
        overflow-x: hidden;
        text-overflow:ellipsis; 
        color: #ccc;      
    }

    .plusMoins{
        border: 0px;
        display: inline-block;
        width: auto;
        padding: 3px;
        background-color: inherit;
        color: #ccc;
        cursor: pointer;
        font-weight: bold;
        font-size: 12px;
        transition: text-decoration 0.3s ease-out;
    }

    .plusMoins:hover{
        text-decoration: underline;
    }


</style>