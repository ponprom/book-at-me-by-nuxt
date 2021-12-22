<template>
  <div>
    <book-layout :book-list="comics" :page-size="18"/>
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
      current: 1,
      pageSize: 18,
      comics: [
        {
          isbn: '9786164318861',
          bookNameTh: 'ยอดกุ๊กแดนมังกร ภาค พิชิตฉงชิ่ง 1',
          bookNameEn: 'Chuuka Ichiban 1',
          price: 55,
          authors: 'ETSUSHI OGAWA',
          genre: '1,2,3',
          type: 3,
          desc: 'อยากจะบรรลุอาหารจีนให้ถึงที่สุด!! ประเทศจีนช่วงปลายราชวงศ์ชิง เหมา เด็กหนุ่มอายุน้อยที่สุดในประวัติศาสตร์ได้เป็น [พ่อครัวชั้นพิเศษ] ซึ่งเป็นจุดสูงสุดของคนทําอาหาร ความฝันใหม่ของเขาคือ [ศึกษาอาหารชนิดใหม่ที่ยังไม่เคยเห็นมาก่อนให้ลึกซึ้งและสร้างสะพานแห่งรสชาติให้กับผู้คน]!!เพื่อที่จะเข้าร่วมการทําบุญครบรอบวันตายของ "พ่อครัวในตํานาน" เหมากับพวกพ้องจึงไปยังบ้านเกิดที่มณฑลซื่อชวน (เสฉวน) ด้วยความตื่นเต้น แต่สิ่งที่รออยู่ก็คือปริศนาและแผนการซึ่งเกี่ยวข้องกับ "พ่อที่ตายไปแล้ว"',
          img: ' https://drive.google.com/uc?export=view&id=1vlA2qmZbD8dsJ5OFuCri7KKo0dT_qoj4'
        }
      ]
    }
  },
  created() {
    this.addNewComic()
  },
  methods: {
    addNewComic() {
      for (let index = 0; index < 40; index++) {
        this.comics.push({
          isbn: '9786164318861' + index,
          bookNameTh: 'ยอดกุ๊กแดนมังกร ภาค พิชิตฉงชิ่ง 1',
          bookNameEn: 'Chuuka Ichiban 1',
          price: 55,
          authors: 'ETSUSHI OGAWA',
          genre: [1,2,3],
          type: 3,
          desc: 'อยากจะบรรลุอาหารจีนให้ถึงที่สุด!! ประเทศจีนช่วงปลายราชวงศ์ชิง เหมา เด็กหนุ่มอายุน้อยที่สุดในประวัติศาสตร์ได้เป็น [พ่อครัวชั้นพิเศษ] ซึ่งเป็นจุดสูงสุดของคนทําอาหาร ความฝันใหม่ของเขาคือ [ศึกษาอาหารชนิดใหม่ที่ยังไม่เคยเห็นมาก่อนให้ลึกซึ้งและสร้างสะพานแห่งรสชาติให้กับผู้คน]!!เพื่อที่จะเข้าร่วมการทําบุญครบรอบวันตายของ "พ่อครัวในตํานาน" เหมากับพวกพ้องจึงไปยังบ้านเกิดที่มณฑลซื่อชวน (เสฉวน) ด้วยความตื่นเต้น แต่สิ่งที่รออยู่ก็คือปริศนาและแผนการซึ่งเกี่ยวข้องกับ "พ่อที่ตายไปแล้ว"',
          img: ' https://drive.google.com/uc?export=view&id=1vlA2qmZbD8dsJ5OFuCri7KKo0dT_qoj4'
        })
      }
    },
    onChange(v) {
      this.current = v
    }
  }
}
</script>

<style></style>
