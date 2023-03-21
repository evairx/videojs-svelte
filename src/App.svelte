<script>
  import { onMount, onDestroy } from 'svelte';
  import videojs from 'video.js'; // We import VideoJs
  import 'video.js/dist/video-js.css'; // Import the videojs styles

  import Menu from './assets/header.svelte'

  let player;

  let source = "https://v.animethemes.moe/BokuNoHeroAcademiaS3-OP1-NCBD1080.webm" // here is the url of the mp4 video

  onMount(() => { // The onMount function is called when the component is mounted. Inside this function
    player = videojs('player', { // the videojs function is called passing a player id and an object with player configuration options like autoplay, controls, nativeControlsForTouch, width, height, and sources. The sources option is an array that contains the src and type of the video that will be played by the player.
      autoplay: true,
      controls: true,
      nativeControlsForTouch: false,
      width: 640,
      height: 360,
      sources: [
        {
          src: source,
          type: 'video/mp4',
        }
      ]
    });
  });

  onDestroy(() => { // The onDestroy function is called when the component is destroyed. Inside this function, the player.dispose() method is called to dispose of the player instance.
    if (player) {
      player.dispose();
    }
  });

</script>

<Menu/>

<main>
  <div class="container">
    <a href="https://github.com/evairx/videojs-svelte"> <i class="fa-solid fa-chevron-left"></i> back to repository</a> <h1>VideoJS with Svelte</h1>
  </div>

  <video id="player" class="video-js vjs-default-skin background"/>

  <p>You can apply this simple code in your Svelte code :3</p>
</main>

<style>
  main {
    margin: 0 auto;
    text-align: center;
  }

  .container {
    display:flex;
    align-items: center;
    justify-content: center;
  }

  .container a {
    text-decoration: none;
    font-size: 18px;
    font-weight: 600;
    margin-right: 10px;
    color:#bebebe;
  }

  .container a:hover {
    color:#fff;
    transition: all 0.3s;
  }

  .background {
    -webkit-box-shadow: 0px 0px 21px 2px #000000; 
box-shadow: 0px 0px 21px 2px #000000;
  }
</style>