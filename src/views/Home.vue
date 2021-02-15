<template>

  <article>
    <div class="articla-col" v-for="(item, index) in videos" :key="index">
      <a :href="`/video/${item.id}`">
        <Card :item="item"></Card>
      </a>
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
      this.axios.get(`https://youtube.googleapis.com/youtube/v3/videos?part=snippet%2CcontentDetails%2Cstatistics&chart=mostPopular&regionCode=TH&maxResults=20&key=${process.env.VUE_APP_YT_API}`).then(res => {
        console.log(res.data)
        this.videos = res.data.items
      })
    },
  }
</script>