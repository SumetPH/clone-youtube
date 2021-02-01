<template>
  <section>
    <aside>
      <div class="aside-menu">
        <img class="aside-icon" src="https://office.mustplay.in.th/static/thumb/2020/10/25/attach-1606277639569.jpg"
          alt="">
        <span>Home</span>
      </div>
      <div class="aside-menu">
        <img class="aside-icon" src="https://office.mustplay.in.th/static/thumb/2020/10/25/attach-1606277639569.jpg"
          alt="">
        <span>Hot</span>
      </div>
      <div class="aside-menu">
        <img class="aside-icon" src="https://office.mustplay.in.th/static/thumb/2020/10/25/attach-1606277639569.jpg"
          alt="">
        <span>Follow</span>
      </div>
    </aside>

    <article>
      <div class="articla-col" v-for="(item, index) in videos" :key="index">
        <Card :item="item"></Card>
      </div>
    </article>

  </section>
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

<style>
  section {
    display: flex;
  }

  aside {
    background-color: rgba(0, 0, 0, 0.9);
    padding: 12px 0px;
    width: 260px;
  }

  .aside-menu {
    height: 40px;
    padding: 0px 24px;
    display: flex;
    align-items: center;
    color: white;
    cursor: pointer;
  }

  .aside-menu:hover {
    background-color: rgba(0, 0, 0, 0.8);
  }

  .aside-icon {
    width: 24px;
    height: 24px;
    border-radius: 50%;
    margin-right: 24px;
  }

  article {
    background-color: black;
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    color: white;
    padding: 1rem 5rem;
  }

  .articla-col {
    width: 100%;
    padding: 1rem;
    box-sizing: border-box;
  }

  @media (max-width: 768px) {
    aside {
      display: none;
    }
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