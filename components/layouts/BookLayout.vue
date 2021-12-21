<template>
  <div>
    <div class="min-h-screen">
      <template v-for="(c, i) in bookList">
        <div
          v-if="i >= pageSize * (current - 1) && i < current * pageSize"
          :key="i"
          class="inline-block h-56 p-2 sm:w-full md:w-1/4 lg:w-1/6 xl:w-1/6"
        >
          <div class="bg-slate-500 h-full">
            {{ i }}
          </div>
        </div>
      </template>
    </div>
    <div class="text-center">
      <a-pagination
        v-model="current"
        :page-size="pageSize"
        :total="bookList.length"
        show-less-items
        @change="onChange"
      />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    bookList: {
      type: Array,
      default: null
    }
  },
  data() {
    return {
      current: 1,
      pageSize: 18
    }
  },
  methods: {
    onChange(v) {
      this.current = v
    }
  }
}
</script>

<style></style>
