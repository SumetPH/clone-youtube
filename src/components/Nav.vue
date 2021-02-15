<template>
  <nav>
    <div class="nav">
      <div class="nav-left">
        <div class="nav-menu">
          <div></div>
          <div></div>
          <div></div>
        </div>
        <div class="nav-title">
          <a style="display: flex; align-items: center; gap: 0.4rem" href="/">
            <img style="width: 24px;" src="@/assets/youtube.png" alt="">
            <b>YouTube</b>
          </a>
        </div>
      </div>

      <div class="nav-center">
        <form action="#">
          <input class="nav-search-input" type="text" placeholder="Search...">
          <button class="nav-search-submit" type="submit">Search</button>
        </form>
      </div>

      <div class="nav-right">
        <span class="nav-profile-title">SumetPH</span>
        <img class="nav-profile-img"
          src="https://office.mustplay.in.th/static/thumb/2020/10/25/attach-1606277632077.jpg" alt="">
      </div>
    </div>
  </nav>
</template>

<style>
  .nav {
    background-color: rgba(0, 0, 0, 0.9);
    color: white;
    height: 56px;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .nav-left,
  .nav-right {
    display: flex;
    align-items: center;
  }

  .nav-menu {
    display: inline-block;
    margin-left: 2rem;
    cursor: pointer;
  }

  .nav-menu div {
    width: 16px;
    height: 2px;
    background-color: white;
    margin: 3px 0px;
    border-radius: 8px;
  }

  .nav-title {
    margin-left: 2rem;
  }

  .nav-search-input {
    width: 500px;
    height: 26px;
    display: inline-block;
    background-color: rgba(0, 0, 0, 0.8);
    outline: none;
    border: none;
    color: white;
  }

  .nav-search-submit {
    width: 65px;
    height: 32px;
    display: inline-block;
    background-color: rgb(50, 50, 50);
    outline: none;
    border: none;
    color: white;
    cursor: pointer;
  }

  .nav-profile-title {
    margin-right: 2rem;
  }

  .nav-profile-img {
    width: 32px;
    height: 32px;
    margin-right: 2rem;
    border-radius: 50%;
  }

  @media (max-width: 990px) {
    .nav-center {
      display: none;
    }
  }
</style>