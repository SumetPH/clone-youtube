<template>
  <!-- <h3>Video</h3> -->
  <div style="width: 100%;">
    <div style="width: 60%;">
      <div class="video">
        <iframe class="player" type="text/html" :src="`http://www.youtube.com/embed/${$route.params.id}`"
          frameborder="0"></iframe>
      </div>
    </div>
  </div>
</template>

<style>
  .video {
    position: relative;
    width: 100%;
    padding-top: 56.25%;
  }

  .player {
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
  }
</style>