<template>
  <el-menu
    class="el-menu-vertical-demo"
    @select="handleMenuClick"
    >
    <template v-for="menu in menuList">
      <el-submenu v-if="menu.children && menu.children.length > 0" :key="`level1${menu.title}`" :index="`level1${menu.title}`">
        <template slot="title">
          <i :class="menu.icon"></i>
          <span>{{ menu.title }}</span>
        </template>
        <template v-for="menuChild in menu.children">
          <el-submenu v-if="menuChild.children && menuChild.children.length > 0" :key="`level2${menuChild.title}`" :index="`level2${menuChild.title}`">
            <template slot="title">
              <i :class="menuChild.icon"></i>
              <span>{{ menuChild.title }}</span>
            </template>
            <template v-for="menuChildChild in menuChild.children">
              <el-menu-item :key="`level3${menuChildChild.title}`" :index="menuChildChild.path">
                <i :class="menuChildChild.icon"></i>
                <span slot="title">{{ menuChildChild.title }}</span>
              </el-menu-item>
            </template>
          </el-submenu>
          <el-menu-item v-else :key="`level2${menuChild.title}`" :index="menuChild.path">
            <i :class="menuChild.icon"></i>
            <span slot="title">{{ menuChild.title }}</span>
          </el-menu-item>
        </template>
      </el-submenu>
      <el-menu-item v-else :key="`level1${menu.title}`" :index="menu.path">
        <i :class="menu.icon"></i>
        <span slot="title">{{ menu.title }}</span>
      </el-menu-item>
    </template>
  </el-menu>
</template>

<script>
export default {
  data() {
    return {
      menuList: [
        {
          icon: 'form',
          path: '/table',
          title: '表格'
        },
        {
          icon: 'form',
          title: '嵌套路由',
          children: [
            {
              icon: '',
              title: 'level1',
              path: '/level1',
              children: [
                {
                  icon: '',
                  title: 'level2',
                  path: '/level1/level2',
                }
              ]
            }
          ]
        }
      ]
    }
  },
  methods: {
    handleMenuClick(index, path) {
      if (!index) {
        return
      }
      console.log(index, path, 'handleMenuClick', this)
      this.$router.push(index)
    }
  }
}
</script>