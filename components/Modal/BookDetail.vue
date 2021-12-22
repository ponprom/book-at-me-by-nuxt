<template>
  <div>
    <a-modal
      :footer="false"
      :visible="visible"
      :title="item && item.bookNameTh"
      @cancel="handleCancel"
    >
      <div class="text-center">
        <div class="flex justify-center">
          <div style="height: 250px; width: 172px">
            <img
              :src="item && item.img"
              class="w-full h-full"
              style="border: 1px solid #ddd"
            />
          </div>
        </div>

        <div class="mt-8">{{ item && item.desc }}</div>
      </div>
    </a-modal>
  </div>
</template>

<script>
export default {
  props: {
    item: {
      type: Object,
      default: null
    },
    visible: {
      type: Boolean,
      default: null
    }
  },
  methods: {
    handleCancel() {
      this.$emit('cancel')
    }
  }
}
</script>

<style></style>
