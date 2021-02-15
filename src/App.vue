<template>
  <Layout>
    <router-view />
  </Layout>
</template>

<script>
  import Layout from '@/components/Layout.vue'
  export default {
    components: {
      Layout
    }
  }
</script>

<style lang="scss">
  @import '@/css/main.scss';
</style>