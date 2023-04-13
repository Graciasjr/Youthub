<script>
    import deo from "$lib/video/1.mp4";
    import imgs from "$lib/images/IDENTITE.jpeg";
    import Fa from "svelte-fa";
    import {faPlay,faEye  } from '@fortawesome/free-solid-svg-icons';

    const options = {
	method: 'GET',
	headers: {
		'X-RapidAPI-Key': 'd51922a2aamsh76bd6178b23307fp1d3696jsn5a68d0737b59',
		'X-RapidAPI-Host': 'youtube-v31.p.rapidapi.com'
	}
};

   let Suggestions = fetch('https://youtube-v31.p.rapidapi.com/captions?part=snippet&videoId=M7FIvfx5J10', options)
        .then(response => response.json())
        .then(response => console.log(response))
        .catch(err => console.error(err));

    let suggestionVideo =[
        {
            "kind": "youtube#searchResult",
            "id": {
                "kind": "youtube#video",
                "videoId": "PiX_y7DlbJU"
            },
            "snippet": {
                "publishedAt": "2023-03-22T13:15:05Z",
                "channelId": "UCk35YdCoXoFSEEiU-MUeMAQ",
                "title": "2023 New Songs ( Best English Songs 2023 ) 🥒 Pop Music 2023 New Songs 🍀 New Popular Songs 2023",
                "description": "2023 New Songs ( Best English Songs 2023 ) Pop Music 2023 New Songs New Popular Songs 2023 Thanks for watching ...",
                "thumbnails": {
                    "default": {
                        "url": "https://i.ytimg.com/vi/PiX_y7DlbJU/default.jpg",
                        "width": 120,
                        "height": 90
                    },
                    "medium": {
                        "url": "https://i.ytimg.com/vi/PiX_y7DlbJU/mqdefault.jpg",
                        "width": 320,
                        "height": 180
                    },
                    "high": {
                        "url": "https://i.ytimg.com/vi/PiX_y7DlbJU/hqdefault.jpg",
                        "width": 480,
                        "height": 360
                    }
                },
                "channelTitle": "Pop internacional",
                "liveBroadcastContent": "none",
                "publishTime": "2023-03-22T13:15:05Z"
            }
        },
        {
            "kind": "youtube#searchResult",
            "id": {
                "kind": "youtube#video",
                "videoId": "PiX_y7DlbJU"
            },
            "snippet": {
            "publishedAt": "2023-03-22T13:15:05Z",
            "channelId": "UCk35YdCoXoFSEEiU-MUeMAQ",
            "title": "2023 New Songs ( Best English Songs 2023 ) 🥒 Pop Music 2023 New Songs 🍀 New Popular Songs 2023",
            "description": "2023 New Songs ( Best English Songs 2023 ) Pop Music 2023 New Songs New Popular Songs 2023 Thanks for watching ...",
            "thumbnails": {
                "default": {
                    "url": "https://i.ytimg.com/vi/PiX_y7DlbJU/default.jpg",
                    "width": 120,
                    "height": 90
                },
                "medium": {
                    "url": "https://i.ytimg.com/vi/PiX_y7DlbJU/mqdefault.jpg",
                    "width": 320,
                    "height": 180
                },
                "high": {
                    "url": "https://i.ytimg.com/vi/PiX_y7DlbJU/hqdefault.jpg",
                    "width": 480,
                    "height": 360
                }
            },
            "channelTitle": "Pop internacional",
            "liveBroadcastContent": "none",
            "publishTime": "2023-03-22T13:15:05Z"
            }
        },
        {
            "kind": "youtube#searchResult",
            "id": {
                "kind": "youtube#video",
                "videoId": "abZJ_wC_kHg"
            },
            "snippet": {
                "publishedAt": "2023-03-22T13:00:02Z",
                "channelId": "UCHACJmUimC9bVxR6_e9GlHQ",
                "title": "Powerful Aggressive Battle Music: &quot;EXODUS&quot; by Robert Slump",
                "description": "(Light Version) Industrial Epic Heavy Aggressive Battle Action Metal Orchestral Rock Doom-like Music. Composed By: Robert ...",
                "thumbnails": {
                    "default": {
                        "url": "https://i.ytimg.com/vi/abZJ_wC_kHg/default.jpg",
                        "width": 120,
                        "height": 90
                    },
                    "medium": {
                        "url": "https://i.ytimg.com/vi/abZJ_wC_kHg/mqdefault.jpg",
                        "width": 320,
                        "height": 180
                    },
                    "high": {
                        "url": "https://i.ytimg.com/vi/abZJ_wC_kHg/hqdefault.jpg",
                        "width": 480,
                        "height": 360
                    }
                },
                "channelTitle": "MrEpicOSTs",
                "liveBroadcastContent": "none",
                "publishTime": "2023-03-22T13:00:02Z"
            }
        },
        {
            "kind": "youtube#searchResult",
            "id": {
                "kind": "youtube#video",
                "videoId": "3D-ixUMcTPY"
            },
            "snippet": {
                "publishedAt": "2023-03-22T13:00:08Z",
                "channelId": "UC7ovu6a8ydIbDy0fAKmoZ9A",
                "title": "鼓鼓 呂思緯 GBOYSWAG [ 好了啦 Piss Off ] Official Music Video",
                "description": "壓力不再山大這首超級紓壓鼓鼓呂思緯2023首波爆炸系單曲〈好了啦〉 #GBOYSWAG is coming back 線上 ...",
                "thumbnails": {
                    "default": {
                        "url": "https://i.ytimg.com/vi/3D-ixUMcTPY/default.jpg",
                        "width": 120,
                        "height": 90
                    },
                    "medium": {
                        "url": "https://i.ytimg.com/vi/3D-ixUMcTPY/mqdefault.jpg",
                        "width": 320,
                        "height": 180
                    },
                    "high": {
                        "url": "https://i.ytimg.com/vi/3D-ixUMcTPY/hqdefault.jpg",
                        "width": 480,
                        "height": 360
                    }
                },
                "channelTitle": "相信音樂BinMusic",
                "liveBroadcastContent": "none",
                "publishTime": "2023-03-22T13:00:08Z"
            }
        },

    ]
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
    {#each suggestionVideo as video }
        <div class="container">
            <div class="video">
            <a href="../watch/{video.id.videoId}">
                <video
                    poster="{video.snippet.thumbnails.high.url}"
                    width="150"
                    height="90"
                    src="https://youtube.com/{video.id.videoId}"
                    bind:duration={duration}
                    >
                    <track kind="captions"/>
                </video>
            </a>
            <span class="time">{timerConvert(duration)}</span>
            <span class="play">
                <Fa icon={faPlay} size="0.5x"></Fa>
            </span>
            </div>
            <div class="video-info">
                <span class="title">{video.snippet.title}</span>
                <div class="body">
                    <img width="20" height="20" src="{imgs}" alt="">
                    <span class="channel-name">{video.snippet.channelTitle}</span>
                </div>
                <span class="vues">
                    <Fa icon={faEye}></Fa>
                    150k vues
                </span>
            </div>
        </div>
    {/each}
</div>



<style>

    .main{
        padding-top: 10px;
    }

    .container{
        /* border-bottom: 1px solid #cccc; */
        width: 100%;
        height: 100px;
        display: flex;
        padding: 15px 5px 2px 5px;
        align-items: center;
        gap: 7px;
    }

    .video{
        position: relative;
    }
    
    .video a{
        text-decoration: none;
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
        top:0;
        left:0;
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
        /* border: 1px solid green; */
        width: 97%;
        height: 100%;
        display: flex;
        padding-top: 7px;
        padding-right: 7px;
        padding-left: 7px;
        flex-direction: column;
        overflow: hidden;
        justify-content: space-between;
        gap: 10px;
    }

    .video-info .title{
        color: #f1f1f1;
        width: 97%;
        font-size: 12px;
        white-space: nowrap;
        overflow: hidden;
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