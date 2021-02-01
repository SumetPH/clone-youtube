<template>
  <div>
    <img style="width: 100%;" :src="item.snippet.thumbnails.medium.url" alt="">
    <p class="card-title">{{item.snippet.title}}</p>
    <p class="card-subtitle">{{item.snippet.channelTitle}}</p>
    <p class="card-subtitle">การดู {{kFormatter(item.statistics.viewCount)}} ครั้ง</p>
  </div>
</template>

<script>
  export default {
    props: ['item'],
    methods: {
      kFormatter(num) {
        if (num >= 1000000) {
          return (num / 1000000).toFixed(1).replace(/\.0$/, '') + ' ล้าน';
        }
        if (num >= 100000) {
          return (num / 100000).toFixed(1).replace(/\.0$/, '') + ' แสน';
        }
        if (num >= 10000) {
          return (num / 10000).toFixed(1).replace(/\.0$/, '') + ' หมื่น';
        }
        if (num >= 1000) {
          return (num / 1000).toFixed(1).replace(/\.0$/, '') + ' พัน';
        }
        return num;
      }
    },
  }
</script>

<style>
  .card-title {
    margin: .3rem 0rem;
  }

  .card-subtitle {
    color: rgba(255, 255, 255, 0.6);
    font-size: 14px;
  }
</style>