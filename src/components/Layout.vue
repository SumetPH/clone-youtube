<template>

  <Nav></Nav>

  <section>
    <aside>
      <div :class="asideMenu()">
        <img class="aside-icon" src="https://office.mustplay.in.th/static/thumb/2020/10/25/attach-1606277639569.jpg"
          alt="">
        <a href="/">Home</a>
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

    <slot></slot>

  </section>


</template>

<script>
  import Nav from '@/components/Nav.vue'
  export default {
    components: {
      Nav
    },
    methods: {
      asideMenu() {
        return this.$route.name === 'Home' ? 'aside-menu-active' : 'aside-menu'
      }
    },
  }
</script>