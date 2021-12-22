<template>
  <div>
    <div class="min-h-screen">
      <div class="flex justify-end mr-4 mb-2">
        <a-icon
          :style="{ fontSize: '20px' }"
          :type="`${grid ? 'unordered-list' : 'appstore'}`"
          class="cursor-pointer"
          @click="changeLayout"
        />
      </div>
      <template v-for="(c, i) in bookList">
        <div
          v-if="i >= pageSize * (current - 1) && i < current * pageSize"
          :key="i"
          :class="`${
            grid ? 'sm:w-full md:w-1/4 lg:w-1/6 xl:w-1/6' : 'w-full'
          } inline-block p-2 `"
          :style="`${grid ? 'height: 350px' : 'height: 190px'}`"
          @click="showDetail(c)"
        >
          <div
            :class="`${
              grid ? 'flex-col' : 'w-full'
            } flex  justify-items-center p-3 h-full shadow-md cursor-pointer hover:shadow-xl`"
          >
            <div
              :class="`${grid ? '' : 'mr-3'}`"
              :style="`${
                grid
                  ? 'height: 250px; width: 172px'
                  : 'height: 150px; width: 72px'
              } truncate`"
            >
              <img
                :src="c.img"
                class="w-full h-full"
                style="border: 1px solid #ddd"
              />
            </div>
            <div
              :class="`flex ${grid ? '' : 'justify-between w-full'}`"
              class=""
            >
              <div :class="`${grid ? ' mt-3' : 'text-lg mt-4'}`">
                {{ c.bookNameTh }}
              </div>
              <div :class="`${grid ? ' mt-3 ml-2 mr-2' : ''}`">
                <a-icon type="heart" class="hover:text-red-500" :style="{ fontSize: '17px' }" />
              </div>
            </div>
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

    <book-layout
      :item="bookItem"
      :visible="modalVisible"
      @cancel="handleCancel"
    />
  </div>
</template>

<script>
import BookLayout from '@/components/Modal/BookDetail'
export default {
  components: {
    BookLayout
  },
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
      current: 1,
      grid: true,
      bookItem: null,
      modalVisible: false
    }
  },
  methods: {
    onChange(v) {
      this.current = v
    },
    changeLayout() {
      this.grid = !this.grid
    },
    showDetail(v) {
      this.modalVisible = !this.modalVisible
      this.bookItem = v
    },
    handleCancel() {
      this.modalVisible = !this.modalVisible
    }
  }
}
</script>

<style></style>
