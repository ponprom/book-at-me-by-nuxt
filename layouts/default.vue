<template>
  <div>
    <a-layout id="components-layout-demo-custom-trigger">
      <side-menu @path="getPath" />
      <a-layout>
        <a-layout-header><app-header /></a-layout-header>
        <!-- <a-breadcrumb class="ml-5 mt-3">
          <a-breadcrumb-item>{{ path }}</a-breadcrumb-item>
        </a-breadcrumb> -->
        <a-layout-content id="content-style">
          <nuxt />
        </a-layout-content>
        <a-layout-footer>Footer</a-layout-footer>
      </a-layout>
    </a-layout>
  </div>
</template>

<script>
import AppHeader from '@/components/layouts/AppHeader'
import SideMenu from '@/components/layouts/SideMenu'
export default {
  components: {
    AppHeader,
    SideMenu
  },
  data() {
    return {
      collapsed: false,
      path: '/Home'
    }
  },
  created() {},
  methods: {
    getCollapsed(v) {
      this.collapsed = v
    },
    getPath(v) {
      if (v === '/') this.path = '/Home'
      this.path = v
    }
  }
}
</script>

<style>
#components-layout-demo-custom-trigger .trigger {
  font-size: 18px;
  line-height: 64px;
  padding: 0 24px;
  cursor: pointer;
  transition: color 0.3s;
}

#components-layout-demo-custom-trigger .trigger:hover {
  color: #1890ff;
}

#components-layout-demo-custom-trigger .logo {
  height: 32px;
  background: rgba(255, 255, 255, 0.2);
  margin: 16px;
}

#content-style {
  margin: 24px 16px;
  padding: 24px;
  background: #fff;
  min-height: 100vh;
}
</style>
