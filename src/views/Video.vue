<template>
  <div class="video" style="width: 100%; display: flex;">
    <div style="width: 70%;">
      <div class="video-player">
        <iframe class="player" type="text/html" :src="`http://www.youtube.com/embed/${$route.params.id}`"
          frameborder="0"></iframe>
      </div>
      <div>
        <p>{{title}}</p>

        <div style="width: 100%; display: flex;">
          <div style="width: 80%; color: gray;">
            <p>การดู {{addCommaInViews(views)}} ครั้ง • {{convertDate(publishedAt)}}</p>
          </div>

          <div style="width: 20%; text-align: center; color: gray;">
            <span>L {{kFormatter(likeCount)}}</span>
            <span style="margin-left: 1rem;">D {{kFormatter(dislikeCount)}}</span>
            <div class="progressbar" style="width: 100%; height: 3px; background-color: gray;">
              <div class="progressbar-like" :style="`width: ${progressLike()}%; height: 3px; background-color: red;`">
              </div>
            </div>
          </div>
        </div>

        <hr style="border-color: gray; margin: 0.5rem 0rem;">

        <div style="margin-bottom: 3rem;">
          <p style="margin: 1rem 0;">{{channelTitle}}</p>
          <pre style="font-size: 0.9rem;">{{description}}</pre>
        </div>
      </div>
    </div>
    <div style="width: 30%;">

    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        title: '',
        views: 0,
        likeCount: 0,
        dislikeCount: 0,
        publishedAt: '',
        channelTitle: '',
        description: ''
      }
    },
    created() {
      this.axios.get(`https://youtube.googleapis.com/youtube/v3/videos?part=snippet%2CcontentDetails%2Cstatistics&id=${this.$route.params.id}&key=${process.env.VUE_APP_YT_API}`).then(res => {
        console.log(res.data)
        const item = res.data.items[0]
        this.title = item.snippet.title
        this.views = item.statistics.viewCount
        this.likeCount = item.statistics.likeCount
        this.dislikeCount = item.statistics.dislikeCount
        this.publishedAt = item.snippet.publishedAt
        this.channelTitle = item.snippet.channelTitle
        this.description = item.snippet.description
      })
    },
    methods: {
      addCommaInViews(views) {
        return parseInt(views).toLocaleString()
      },
      convertDate(d) {
        const nd = new Date(d)
        const date = nd.getDate()
        const month = nd.toLocaleString('th-TH', { month: 'long' });
        const year = nd.getFullYear()
        return `${date} ${month} ${year}`
      },
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
      },
      progressLike() {
        const x = parseInt(this.likeCount) * 100
        const y = parseInt(this.likeCount) + parseInt(this.dislikeCount)
        return x / y
      }
    }
  }
</script>