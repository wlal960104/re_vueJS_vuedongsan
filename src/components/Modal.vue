<template>
   <div class="black-bg" v-if="isModal === true">
    <div class="white-bg">
      <img :src="prodList[prodId].image" alt="prod-image" style="width:100%">
      <h4>{{prodList[prodId].title}}</h4>
      <p>{{prodList[prodId].content}}</p>
      <p>{{prodList[prodId].price}} 원</p>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Modal',
  props: {
    prodList: Array,
    prodId: Number,
    isModal: Boolean
  }
}
</script>

<style>

</style>