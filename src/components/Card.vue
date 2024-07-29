<template>
  <!-- 상품 영역 -->
  <div>
    <img :src="prodData.image" alt="room_img" class="room-img">
    <h4 @click="openModal">{{prodData.title}}</h4>
    <p>{{prodData.price}}원</p>
    <button @click="report">허위매물신고</button><br>
    <span>신고수 : {{count}}</span>
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
    // 모달창 열기
    openModal() {
      this.$emit('openModal', this.prodData.id)
    },
    // [허위매물신고] 버튼 클릭
    report() {
      this.$emit('report', this.prodData.id)
    }
  }
}
</script>

<style>

</style>