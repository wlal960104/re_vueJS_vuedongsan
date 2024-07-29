<template>
  <!-- 상품 리스트 영역 -->
  <div>
    <img :src="prodData.image" alt="room_img" class="room-img">
    <!--<h4 @click="isModal = true; prodId = i;">{{prodData.title}}</h4>-->
    <h4 @click="openModal">{{prodData.title}}</h4>
    <p>{{prodData.price}}원</p>
    <!--<button @click="increase(i)">허위매물신고</button><br>-->
    <!--<span>신고수 : {{count[i]}}</span>-->
  </div>
</template>

<script>
export default {
  name: 'Card',
  props : {
    prodData : Object, // 상품리스트의 상품 1개
    count : Number, // 신고 수

  },
  methods : {
    openModal() {
      this.$emit('openModal', this.prodData.id)
    }
  }
}
</script>

<style>

</style>