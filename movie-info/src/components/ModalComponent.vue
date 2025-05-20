<template>
  <div class="modal" v-if="isModal">
    <div class="inner">
      <h3>{{ movieData[selectMovie].title }}</h3>
      <p>영화 상세정보</p>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>
//:data="movieData" :isModal="isModal" :selectMovie="selectMovie"
<script>
export default {
  name: "ModalComponets",
  props: {
    movieData: Array,
    isModal: Boolean,
    selectMovie: Number,
  },
};
</script>

<style lang="scss" scoped></style>
