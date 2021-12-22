<template>
  <a-layout-sider
    id="sider-style"
    v-model="collapsed"
    class="text-slate-300"
    :trigger="null"
    collapsible
  >
    <a-icon
      class="trigger"
      :type="collapsed ? 'menu-unfold' : 'menu-fold'"
      @click="handleCollapsed"
    />
    <a-menu theme="dark" mode="inline" :default-selected-keys="['1']">
      <a-menu-item v-for="m in menu" :key="m.key" @click="cilckMenu">
        <nuxt-link :to="m.path">
          <a-icon :type="m.icon" />
          <span>{{ m.name }}</span>
        </nuxt-link>
      </a-menu-item>
    </a-menu>
  </a-layout-sider>
</template>

<script>
export default {
  data() {
    return {
      menu: [
        {
          key: 1,
          name: 'หน้าหลัก',
          path: '/',
          icon: 'home'
        },
        {
          key: 2,
          name: 'การ์ตูน',
          path: '/comic',
          icon: 'book'
        },
        {
          key: 3,
          name: 'นิยาย',
          path: '/novel',
          icon: 'book'
        }
      ],
      collapsed: false
    }
  },
  methods: {
    handleCollapsed() {
      this.collapsed = !this.collapsed
    },
    cilckMenu() {
      this.$emit('path', this.$route.path)
    }
  }
}
</script>

<style></style>
