<script>
    import Fa from 'svelte-fa';
    import deo from "../video/1.mp4";
    import imgs from "$lib/images/IDENTITE.jpeg";
    import { faPlus,faPencil,faCaretDown,faCaretUp } from '@fortawesome/free-solid-svg-icons';
    import PlaylistVideoFormat from './PlaylistVideoFormat.svelte';
    import PocketBase from 'pocketbase';
    
    $:PlayList=[];
    $:playlistBool = false;
    $:playlistName =''
    const pb = new PocketBase('http://127.0.0.1:3000');
    const authData = pb.admins.authWithPassword('graciasdagadgc@gmail.com','dgccompany1243');

    async function playlist(){       
       
        PlayList = await pb.collection('playlist').getFullList(200,{
            sort:'-created'
        });
        console.log(PlayList);

    }

    async function createPlaylist(){
        const data ={
            "playlistName":playlistName,
            "video":[],
            "expanded":false
        }
        const record = await pb.collection('playlist').create(data);
        PlayList =[...[data],...PlayList];
        playlistBool =! playlistBool;
        console.log(PlayList);
    }

    setTimeout(async() => {
        playlist();
    }, 1000);

</script>

<div class="main">
    <div class="header">
        <div class="action">
            <button class="btn" on:click={()=>{playlistBool=!playlistBool}}>
                <Fa icon={faPlus} size="1x"></Fa>
                <span>Nouvelle</span>
            </button>
            {#if playlistBool}
                <div class="playlist-form">
                    <input type="text" bind:value={playlistName}>
                    <button on:click={createPlaylist}>
                        Creer
                    </button>
                </div>                
            {/if}
        </div>
    </div>

    <div class="playlist-container">
        {#each PlayList as list }       
            <div class="playlist">
                <div class="list-header">
                    <span class="playlist-name">{list.playlistName}</span>
                    <button class="caret" on:click={()=>{list.expanded=!list.expanded}}>
                        <Fa icon={faCaretUp}></Fa>
                    </button>
                </div>                               
                <ul id="{list.expanded===true?'':'expanded'}">
                    {#if list.video!==" " }                            
                        {#each list.video as video }                        
                            <li>
                                <PlaylistVideoFormat videoUrl={video.url}></PlaylistVideoFormat>
                            </li>
                        {/each}
                    {/if}
                </ul>                
            </div>
        {/each}
    </div>

</div>

<style>

    .main{
        border: 1px solid royalblue;
        width: 100%;
        min-height: 70vh;
        display: flex;
        flex-direction: column;

    }

    .header{
        /* border: 1px solid crimson; */
        width: 100%;
        height: 7vh;
        display: flex;
        align-items: start;
    }

    .action{
        width: 100% ;
        padding: 3px;
        display: flex;
        align-items: center;
        position: relative;
        cursor: pointer;
    }

    button.btn{
        border: 0px;
        /* background: #ffffff23; */
        background: transparent;
        color: #fff;
        padding: 7px 10px;
        border-radius: 7px;
        display: flex;
        gap: 7px;
        cursor: pointer;
        transition: 0.2s ease-out;
    }

    button.btn:hover{
        background: #ffffff3f;
    }

    .playlist-form{
        border: 1px solid;
        position: absolute;
        width:230px;
        /* height: 250px; */
		display: flex;
		align-items: center;
        padding: 10px;
		gap: 10px;
        left:12%;
        top:35%;
        background: #dddddd18;
        /* backdrop-filter: blur(2px); */
    }

    .playlist-form input{
        width:100%;
        height: 5vh;
        border: none;
        border-radius: 50px;
        padding-left: 13px;
		background:var(--color5);
		color: #fafafa;
		font-family: Calibri;
		font-size: 14px;
		/* outline: none; */
    }

    .playlist-form input:focus{
        outline: auto;
    }

    .playlist-form button{
        border:0px;
        background:#ffffff27;
        padding: 7px 7px;
        position: absolute;
        color: #fff;
        right:10px;
        font-weight: bold;
        border-radius: 50px;
    }

    .playlist-container{
        /* border: 1px solid crimson; */
        height: 100%;
    }

    .playlist{
        border-bottom: 1px solid #cccccc33;
        padding-top: 2px;
        padding-bottom: 7px;
    }

    .list-header{
        width: auto;
        display:flex;
        margin-left: 5px;
        gap: 7px;
        font-size: 13px;
        font-weight: bold;
        cursor: pointer;
    }

    button.caret{
        border:0px;
        padding: 2px;
        width: 10px;
        height: 10px;
        background-color: transparent;
        color: #fafafa;

    }

    .playlist ul{
        list-style: none;
        height: auto;
        padding-left:12px;
        white-space: "";
        overflow-y: hidden;
        transition:all 0.3s ease-out;
    }
    
    #expanded{
        max-height:7px;
    }
    ul li{
        display: inline-block;

    }
</style>