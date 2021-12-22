<template>
  <div>
    <book-layout :book-list="novels" :page-size="18" />
  </div>
</template>

<script>
import BookLayout from '@/components/layouts/BookLayout'
export default {
  components: {
    BookLayout
  },
  data() {
    return {
      novels: [
        {
          isbn: '9786160439232',
          bookNameTh: 'แฮร์รี่ พอตเตอร์กับห้องแห่งความลับ เล่ม 2',
          bookNameEn: 'Harry Potter and the Chamber of Secrets',
          price: 316,
          authors: 'J.K. Rowling (เจ.เค. โรว์ลิ่ง)',
          genre: [13,14,15,16],
          type: 1,
          desc: 'ช่วงหน้าร้อนของแฮรรี่ประกอบด้วยวันเกิดที่แย่ที่สุดที่เขาเคยเจอ คำเตือนที่เป็นลางร้ายจากด๊อบบี้ เอลฟ์ประจำบ้าน และการที่รอน วิสลีย์ เพื่อนรักของเขามาพาเขาหนีจากพวกเดอร์สลีย์ด้วยรถยนต์เหาะได้!เมื่อกลับไปเรียนปีสองที่โรงเรียนคาถาพ่อมดแม่มดและเวทมนตร์ศาสตร์ฮอกวอตส์ แฮรรี่ได้ยินเสียงกระซิบแปลกๆดังสะท้อนจากทางเดินว่างเปล่า แล้วการโจมตีก็เริ่มขึ้น นักเรียนหลายคนถุกพบว่ากลายเป็น หิน...ดูเหมือนว่าคำเตือนอันเป็นลางร้ายของด๊อบบี้กำลังจะกลายเป็นจริง',
          img: ' https://drive.google.com/uc?export=view&id=1W9ObOBHqUZ91uAcYpl28IM9dbm2D_xVL'
        }
      ]
    }
  },
  created() {
    this.addNewNovel()
  },
  methods: {
    addNewNovel() {
      for (let index = 0; index < 15; index++) {
        this.novels.push({
          isbn: '9786164318861' + index,
          bookNameTh: 'แฮร์รี่ พอตเตอร์กับห้องแห่งความลับ เล่ม 2',
          bookNameEn: 'Harry Potter and the Chamber of Secrets',
          price: 316,
          authors: 'J.K. Rowling (เจ.เค. โรว์ลิ่ง)',
          genre: [13,14,15,16],
          type: 1,
          desc: 'ช่วงหน้าร้อนของแฮรรี่ประกอบด้วยวันเกิดที่แย่ที่สุดที่เขาเคยเจอ คำเตือนที่เป็นลางร้ายจากด๊อบบี้ เอลฟ์ประจำบ้าน และการที่รอน วิสลีย์ เพื่อนรักของเขามาพาเขาหนีจากพวกเดอร์สลีย์ด้วยรถยนต์เหาะได้!เมื่อกลับไปเรียนปีสองที่โรงเรียนคาถาพ่อมดแม่มดและเวทมนตร์ศาสตร์ฮอกวอตส์ แฮรรี่ได้ยินเสียงกระซิบแปลกๆดังสะท้อนจากทางเดินว่างเปล่า แล้วการโจมตีก็เริ่มขึ้น นักเรียนหลายคนถุกพบว่ากลายเป็น หิน...ดูเหมือนว่าคำเตือนอันเป็นลางร้ายของด๊อบบี้กำลังจะกลายเป็นจริง',
          img: ' https://drive.google.com/uc?export=view&id=1W9ObOBHqUZ91uAcYpl28IM9dbm2D_xVL'
        })
      }
    }
  }
}
</script>

<style></style>
