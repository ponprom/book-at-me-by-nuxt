<template>
  <div>
    <div class="min-h-screen">
      <!-- <div>
        <a-button :icon="'appstore'" ></a-button>
      </div> -->
      <template v-for="(c, i) in bookList">
        <div
          v-if="i >= pageSize * (current - 1) && i < current * pageSize"
          :key="i"
          class="inline-block p-2 sm:w-full md:w-1/4 lg:w-1/6 xl:w-1/6"
          style="height: 350px"
        >
          <div
            class="flex flex-col justify-items-center p-3 h-full shadow-md cursor-pointer hover:shadow-xl"
          >
            <div style="height: 250px; width: 172px truncate">
              <img
                :src="c.img"
                class="w-full h-full"
                style="border: 1px solid #ddd"
              />
            </div>
            <div class="mt-2">{{ c.bookNameTh }}</div>
          </div>
        </div>
      </template>
    </div>
    <div class="text-center mt-10">
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
    },
    pageSize: {
      type: Number,
      default: null
    }
  },
  data() {
    return {
      current: 1
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
