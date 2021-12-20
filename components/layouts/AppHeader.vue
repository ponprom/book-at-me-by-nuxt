<template>
  <div class="text-slate-300">
    <a-row>
      <a-col :span="18">
        <div>BOOK AT ME</div>
      </a-col>
      <a-col :span="6">
        <div class="flex justify-end">
          <nuxt-link to="/login">
            <div class="mr-3">เข้าสู่ระบบ</div>
          </nuxt-link>
          <nuxt-link to="/register">
            <a-button type="danger" class="bg-red-500 self-center">
              สมัครสมาชิค
            </a-button>
          </nuxt-link>
        </div>
      </a-col>
    </a-row>
  </div>
</template>

<script>
export default {
  data() {
    return {}
  },
  methods: {}
}
</script>

<style></style>
