<template>
  <div>
    <!-- Header -->
    <header class="fixed-top">
      <nav class="navbar navbar-expand-lg navbar-light bg-white">
        <div class="container">
          <button
            class="navbar-toggler"
            type="button"
            data-toggle="collapse"
            data-target="#navbarNav"
            aria-controls="navbarNav"
            aria-expanded="false"
            aria-label="Toggle navigation"
          >
            <span class="navbar-toggler-icon"></span>
          </button>
          <div class="ms-logo">
            <h1 class="m-0">
              <router-link to="/index" class="navbar-brand ml-auto" href="#">MapleStory</router-link>
            </h1>
          </div>
          <div class="collapse navbar-collapse" id="navbarNav">
            <ul class="navbar-nav ml-auto">
              <li class="nav-item">
                <span></span>
                <router-link
                  to="/index"
                  class="nav-link p-3"
                  data-toggle="collapse"
                  data-target=".navbar-collapse.show"
                >
                  <i class="fas fa-home"></i>
                  首頁
                </router-link>
              </li>
              <li class="nav-item">
                <span></span>
                <router-link
                  to="/category"
                  class="nav-link p-3"
                  data-toggle="collapse"
                  data-target=".navbar-collapse.show"
                >
                  <i class="fas fa-box-open"></i>
                  所有商品
                </router-link>
              </li>
              <li class="nav-item">
                <span></span>
                <router-link
                  to="/customerOrder"
                  class="nav-link p-3"
                  data-toggle="collapse"
                  data-target=".navbar-collapse.show"
                >
                  <i class="fas fa-shopping-cart"></i>
                  購物車
                </router-link>
              </li>
              <li class="nav-item">
                <span></span>
                <a class="nav-link p-3" href="https://github.com/Sealman234">
                  <i class="fab fa-github"></i>
                  關於作者
                </a>
              </li>
              <li class="nav-item">
                <span></span>
                <router-link
                  to="/login"
                  class="nav-link p-3"
                  data-toggle="collapse"
                  data-target=".navbar-collapse.show"
                >
                  <i class="fas fa-user-cog"></i>
                  登入
                </router-link>
              </li>
            </ul>
          </div>
        </div>
      </nav>
    </header>
  </div>
</template>

<script>
export default {
  name: "Header"
};
</script>

<style scoped lang="scss">
// Header (選單)
.navbar {
  border-bottom: 4px solid #d3d3d3;
  box-shadow: 0 3px 10px rgba(0, 0, 0, 0.15);
  .ms-logo {
    @media (max-width: 992px) {
      margin: 0 auto;
    }
    .navbar-brand {
      background-image: url(../assets/images/MapleStory.svg);
      width: 150px;
      height: 57.79px;
      display: block;
      text-indent: 101%;
      overflow: hidden;
      white-space: nowrap;
    }
  }
  li.nav-item {
    float: left;
    position: relative;
    &:hover span {
      position: absolute;
      left: 50%;
      top: 50%;
      margin-left: -35%;
      width: 70%;
      height: 0px;
      box-shadow: 0 0 20px 12px rgba(150, 180, 200, 0.6);
      border-radius: 10px 6px;
      @media (max-width: 991px) {
        left: 2%;
        top: 50%;
        margin-left: 0;
        width: 95%;
      }
    }
    .nav-link {
      display: block;
      background: transparent;
      // color: #000;
      font-weight: bold;
      text-decoration: none;
      padding: 20px;
      position: relative;
      &.active,
      &:hover {
        color: #c1170c;
      }
    }
  }
}
</style>
