<template>

  <article>
    <div class="articla-col" v-for="(item, index) in videos" :key="index">
      <router-link :to="`/video/${item.id}`">
        <Card :item="item"></Card>
      </router-link>
    </div>
  </article>


</template>

<script>
  import Card from '@/components/Card.vue'
  export default {
    components: {
      Card
    },
    data() {
      return {
        videos: []
      }
    },
    mounted() {
      this.axios.get(`https://youtube.googleapis.com/youtube/v3/videos?part=snippet%2CcontentDetails%2Cstatistics&chart=mostPopular&regionCode=TH&maxResults=40&key=${process.env.VUE_APP_YT_API}`).then(res => {
        console.log(res.data)
        this.videos = res.data.items
      })
    },
  }
</script>

<style>
  article {
    background-color: black;
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    color: white;
    padding: 1rem 5rem;
    min-height: 100vh;
  }

  article a {
    text-decoration: none;
    color: white;
  }

  .articla-col {
    width: 100%;
    padding: 1rem;
    box-sizing: border-box;
  }

  @media (min-width: 768px) {
    .articla-col {
      width: 50%;
    }
  }

  @media (min-width: 1200px) {
    .articla-col {
      width: 25%;
    }
  }
</style>