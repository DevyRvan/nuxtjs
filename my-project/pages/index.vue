<template>
  <div class="container">
    <div class="container-left">
      <nuxt-link to="/home" class="logo">
        <Logo></Logo>
      </nuxt-link>
      <PageMenu></PageMenu>
    </div>
    <div class="container-right">
      <div class="header">
        <div class="sys-title">{{ sysTitle }}</div>
      </div>
      <div class="right-main">
        <nuxt-child class="main-content"></nuxt-child>
      </div>
    </div>
  </div>
</template>

<script>
import Logo from '../components/Logo.vue'
import PageMenu from '../components/PageMenu'
export default {
  components: { Logo, PageMenu },
  asyncData ({ redirect }) {
    return redirect('/home')
  },
  data() {
    return {
      sysTitle: 'Nuxt element page'
    }
  },
  methods: {
  }
}
</script>

<style lang="scss">
$headerHeight: 80px;
.container {
  position: absolute;
  top: 0;
  bottom: 0;
  color: #666;
  width: 100%;
  vertical-align: top;
  .logo {
    height: $headerHeight;
    width: 100%;
    text-align: center;
    display: block;
    svg {
      display: inline-block;
      width: 50px;
      height: 100%;
    }
  }
}
.container .container-left {
  position: relative;
  left: 0;
  display: inline-block;
  width: 200px;
  height: 100%;
  box-sizing: border-box;
  background: #001529;
  border-right: solid 1px #e6e6e6;
}
.container .container-left .el-menu {
  height: calc(100% - #{$headerHeight});
  border-right: 0;
  background: transparent;
  box-sizing: border-box;
  .el-menu-item {
    color: #ddd;
  }
  .el-menu-item:focus, .el-menu-item:hover {
    outline: 0;
    background-color: #1890ff;
  }
  .el-submenu__title:hover {
    background-color: #1890ff;
  }
  .el-submenu__title {
    color: #ddd;
  }
  .el-menu-item.is-active {
    color: #f1f1f1;
    background-color: #1890ff;
  }
}
.container .container-right {
  position: absolute;
  display: inline-block;
  box-sizing: border-box;
  left: 200px;
  width: calc(100% - 200px);
  height: 100%;
  .header {
    height: $headerHeight;
    line-height: $headerHeight;
    width: 100%;
    box-sizing: border-box;
    border-bottom: 1px solid #e6e6e6;
    .sys-title {
      margin-left: 30px;
      height: 100%;
      font-size: 20px;
      color: #666;
      // font-weight: bolder;
    }
  }
  .right-main {
    height: calc(100% - #{$headerHeight});
    padding: 15px;
    background: #f0f2f5;
    .main-content {
      background: #fff;
      padding: 10px 15px;
      height: 100%;
    }
  }
}
.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
