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
      <a-menu-item key="1">
        <nuxt-link to="/">
          <a-icon type="home" />
          <span>หน้าหลัก</span>
        </nuxt-link>
      </a-menu-item>
      <a-menu-item key="2">
        <nuxt-link to="/comic">
          <a-icon type="book" />
          <span>การ์ตูน</span>
        </nuxt-link>
      </a-menu-item>
      <a-menu-item key="3">
        <nuxt-link to="/novel">
          <a-icon type="book" />
          <span>นิยาย</span>
        </nuxt-link>
      </a-menu-item>
    </a-menu>
  </a-layout-sider>
</template>

<script>
export default {
  data() {
    return {
      collapsed: false
    }
  },
  methods: {
    handleCollapsed() {
      this.collapsed = !this.collapsed
    }
  }
}
</script>

<style></style>
