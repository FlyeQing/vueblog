<template>
  <aside class="left">
    <ul class="menu">
      <li>
        <h3>VueBlog</h3></li>
      <li v-for="item in menu">
        <router-link :to="{path:item.path}">{{item.name}}</router-link>
      </li>
      <li><a @click="logout">退出登录</a></li>
    </ul>
  </aside>
</template>
<script>
export default {
  name:'AdminAside',
  data() {
    return {
      menu: [{
        name: '网站首页',
        path: '/index'
      }, {
        name: '后台首页',
        path: '/admin'
      }, {
        name: '发布文章',
        path: '/publish'
      }, {
        name: '修改信息',
        path: '/updateAdminInfo'
      }, {
        name: '修改密码',
        path: '/updateAdminPassword'
      }]
    }
  },
  methods: {
    logout() {
      this.axios.post('/logout').then((data) => {
        if (data.data.code === 200) {
          this.$router.push({ name: 'index' })
          this.$router.go(0)
        }
      })
    }
  }
}
</script>