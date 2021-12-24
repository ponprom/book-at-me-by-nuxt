<template>
  <div>
    <div><a-button class="mb-2" @click="showBookForm">Add</a-button></div>
    <a-table :columns="columns" :data-source="books">
      <template slot="BookType" slot-scope="value">
        {{ value === 1 ? 'Novel' : 'Comic' }}
      </template>
      <template slot="BookImage" slot-scope="value">
        <div style="height: 150px; width: 92px">
          <img
            :src="value"
            class="w-full h-full"
            style="border: 1px solid #ddd"
          />
        </div>
      </template>
      <template slot="Actions" slot-scope="value">
        <a-button
          icon="edit"
          class="mb-2 bg-orange-300"
          @click="handleEdit(value)"
        ></a-button>
        <a-button
          icon="delete"
          class="bg-red-400"
          @click="handleDelete(value.key)"
        ></a-button>
      </template>
    </a-table>

    <book-form
      :item="item"
      :is-edit="isEdit"
      :visible="modalVisible"
      @cancel="handleCancel"
      @submit="handleSubmit"
    />
  </div>
</template>

<script>
import { cloneDeep } from 'lodash'
import BookForm from '@/components/Modal/BookForm'
export default {
  components: {
    BookForm
  },
  data() {
    return {
      books: [
        {
          key: 1,
          isbn: '9786164318861',
          bookNameTh: 'ยอดกุ๊กแดนมังกร ภาค พิชิตฉงชิ่ง 1',
          bookNameEn: 'Chuuka Ichiban 1',
          price: 55,
          authors: 'ETSUSHI OGAWA',
          genre: [1, 2, 3],
          type: 2,
          desc: 'อยากจะบรรลุอาหารจีนให้ถึงที่สุด!! ประเทศจีนช่วงปลายราชวงศ์ชิง เหมา เด็กหนุ่มอายุน้อยที่สุดในประวัติศาสตร์ได้เป็น [พ่อครัวชั้นพิเศษ] ซึ่งเป็นจุดสูงสุดของคนทําอาหาร ความฝันใหม่ของเขาคือ [ศึกษาอาหารชนิดใหม่ที่ยังไม่เคยเห็นมาก่อนให้ลึกซึ้งและสร้างสะพานแห่งรสชาติให้กับผู้คน]!!เพื่อที่จะเข้าร่วมการทําบุญครบรอบวันตายของ "พ่อครัวในตํานาน" เหมากับพวกพ้องจึงไปยังบ้านเกิดที่มณฑลซื่อชวน (เสฉวน) ด้วยความตื่นเต้น แต่สิ่งที่รออยู่ก็คือปริศนาและแผนการซึ่งเกี่ยวข้องกับ "พ่อที่ตายไปแล้ว"',
          img: ' https://drive.google.com/uc?export=view&id=1vlA2qmZbD8dsJ5OFuCri7KKo0dT_qoj4'
        },
        {
          key: 2,
          isbn: '9786160439232',
          bookNameTh: 'แฮร์รี่ พอตเตอร์กับห้องแห่งความลับ เล่ม 2',
          bookNameEn: 'Harry Potter and the Chamber of Secrets',
          price: 316,
          authors: 'J.K. Rowling (เจ.เค. โรว์ลิ่ง)',
          genre: [13, 14, 15, 16],
          type: 1,
          desc: 'ช่วงหน้าร้อนของแฮรรี่ประกอบด้วยวันเกิดที่แย่ที่สุดที่เขาเคยเจอ คำเตือนที่เป็นลางร้ายจากด๊อบบี้ เอลฟ์ประจำบ้าน และการที่รอน วิสลีย์ เพื่อนรักของเขามาพาเขาหนีจากพวกเดอร์สลีย์ด้วยรถยนต์เหาะได้!เมื่อกลับไปเรียนปีสองที่โรงเรียนคาถาพ่อมดแม่มดและเวทมนตร์ศาสตร์ฮอกวอตส์ แฮรรี่ได้ยินเสียงกระซิบแปลกๆดังสะท้อนจากทางเดินว่างเปล่า แล้วการโจมตีก็เริ่มขึ้น นักเรียนหลายคนถุกพบว่ากลายเป็น หิน...ดูเหมือนว่าคำเตือนอันเป็นลางร้ายของด๊อบบี้กำลังจะกลายเป็นจริง',
          img: ' https://drive.google.com/uc?export=view&id=1W9ObOBHqUZ91uAcYpl28IM9dbm2D_xVL'
        }
      ],
      modalVisible: false,
      item: null,
      isEdit: false
    }
  },
  computed: {
    columns() {
      return [
        {
          title: '#',
          dataIndex: 'img',
          scopedSlots: { customRender: 'BookImage' }
        },
        {
          title: 'Book Name',
          dataIndex: 'bookNameTh'
        },
        {
          title: 'Authors',
          dataIndex: 'authors'
        },
        {
          title: 'Type',
          dataIndex: 'type',
          scopedSlots: { customRender: 'BookType' }
        },
        {
          title: 'Description',
          dataIndex: 'desc'
        },
        {
          title: 'Action',
          width: '90px',
          scopedSlots: { customRender: 'Actions' }
        }
      ]
    }
  },
  methods: {
    handleDelete(key) {
      this.books = this.books.filter((item) => item.key !== key)
    },
    showBookForm() {
      this.modalVisible = !this.modalVisible
    },
    handleEdit(v) {
      this.item = cloneDeep(v)
      this.isEdit = true
      this.modalVisible = !this.modalVisible
    },
    handleCancel() {
      this.item = null
      this.isEdit = false
      this.modalVisible = !this.modalVisible
    },
    handleSubmit(v) {
      if (!this.isEdit) {
        this.books.push(v)
      } else {
        for (let index = 0; index < this.books.length; index++) {
          if (this.books[index].key === v.key) {
            this.books[index].img = v.img
            this.books[index].bookNameTh = v.bookNameTh
            this.books[index].authors = v.authors
            this.books[index].type = v.type
            this.books[index].desc = v.desc
          }
        }
      }
      this.handleCancel()
    }
  }
}
</script>

<style></style>
