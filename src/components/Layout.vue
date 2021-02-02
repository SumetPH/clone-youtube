<template>

  <Nav></Nav>

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

    <slot></slot>

  </section>


</template>

<script>
  import Nav from '@/components/Nav.vue'
  export default {
    components: {
      Nav
    }
  }
</script>

<style>
  * {
    padding: 0;
    margin: 0;
    font-family: Arial, Helvetica, sans-serif;
  }

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

  @media (max-width: 768px) {
    aside {
      display: none;
    }
  }
</style>