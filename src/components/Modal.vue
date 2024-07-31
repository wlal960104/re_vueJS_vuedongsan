<template>
   <div class="black-bg" v-if="isModal === true">
    <div class="white-bg">
      <img :src="prodList[prodId].image" alt="prod-image" style="width:100%">
      <h4>{{prodList[prodId].title}}</h4>
      <p>{{prodList[prodId].content}}</p>
      <input v-model.number="month">
      <p>{{month}}개월 선택함 : {{prodList[prodId].price * month}}원</p>

      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Modal',
  data() {
    return {
      month: 0 // 초기값 잘 설정해야 함
    }
  },
  props: {
    prodList: Array,
    prodId: Number,
    isModal: Boolean
  },
  watch: {
    // month(a,b): 파라미터 2개까지 가능
    // a: 변경 될 값, b: 입력 전 값
    month(a) {
      // if ( a > 12 ){
      //   this.month = 12;
      //   return alert('12개월을 초과할 수 없습니다');
      // }

      // 문자 입력 불가 (한글 모음, 자음 인식 불가)
      // TODO: 개선 필요
      if ( a !== '' && (typeof a === 'string')) {
        this.month = 1;
        alert('숫자만 입력 가능합니다.');
      }
    }
  },
  created() {
    console.log('Modal.vue ::: created > ')

  },
  mounted() {
    console.log('Modal.vue ::: mounted > ')

  },
  beforeUpdate() {
    console.log('Modal.vue ::: beforeUpdate > ')
    console.log('this >>>', this);
    if (this.month === 2) {
      alert('2개월은 입력 불가합니다.');
      this.month = 3;
    }
  }

}
</script>

<style>

</style>