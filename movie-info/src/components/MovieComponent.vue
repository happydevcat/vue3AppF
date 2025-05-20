<template>
  <div>
    <div v-for="movie in movieData" :key="movie.id" clas="item">
      <div class="info">
        <h3 class="bg-yello" :style="movie.textRed">{{ movie.title }}</h3>
        <figure>
          <img :src="`/assets/${movie.title}.jpg`" :alt="movie.title" />
        </figure>

        <h3>{{ movie.year }}</h3>
        <h3>{{ movie.category }}</h3>
        <button @:click="$emit('increseLike', movie.id)">좋아요</button> <span>{{ movie.like }}</span> <br /><button @click="$emit(`openModal`, movie.id)">상세보기</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MovieComponent",
  emits: ["openModal", "increseLike"],
  props: {
    movieData: Array,
  },
};
</script>

<style scoped></style>
