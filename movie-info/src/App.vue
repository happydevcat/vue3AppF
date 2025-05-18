<template>
  <h1>영화정보 </h1>
  <div v-for="(movie,iLoop) in movieData" :key="iLoop" clas="item">

    <div class="info">
      <h3 class="bg-yello" :style="movie.textRed">{{movie.title}} </h3>
     <figure>
      <img :src="`/assets/${movie.title}.jpg`" :alt="movie.title">
    </figure>

      <h3>{{movie.year}} </h3>
      <h3>{{movie.category}} </h3>
      <button @:click="increseLike(iLoop)">좋아요</button> <span>{{ movie.like }}</span>
      <br/><button @click="isModal=true; selectMovie= iLoop">상세보기</button>
    </div>
  </div>

  <div class="modal" v-if="isModal">
    <div class="inner">
      <h3>{{movieData[selectMovie].title}}</h3>
      <p>영화 상세정보</p>
      <button @click="isModal=false">닫기</button>
    </div>
  </div>

</template>

<script>

  import movieData from './assets/movies';
  console.log(movieData);

  export default{
    name : 'App',
    data(){
      return {
        isModal: false,
        movieData: movieData,
        selectMovie: 0
      }

    },

    methods: {
      increseLike(index){
        this.movieData[index].like +=1;
      }
      
    },

    

  }
</script>

<style>

  *{
      box-sizing: border-box;
      margin: 0;
  }

  body{
    max-width: 600px;
    margin: 0 auto;
    padding: 20px;
  }

  h1,h2,h3{
    margin-bottom: 1rem;
  }
  p{margin-bottom: 0.5rem;}

  .bg-yello{
    background: orange;
    padding: 10;

  }
  .item{
    width: 100%;
    border: 1px solid #ccc;
    display: flex;
    margin-bottom: 20px;
    padding: 1rem;
  }
  .item figure{
    width: 30%;
    margin-right: 1rem;
  }
  .item img{
    width: 100%;
  }
  .item .info{
    width:100%;
  }

  .modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.4); /* 반투명 검은 배경 */
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 999;
  animation: fadeIn 0.3s ease;
}

.inner {
  background: #fff0f6;
  border-radius: 20px;
  padding: 30px;
  width: 300px;
  text-align: center;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
  animation: popUp 0.3s ease;
  font-family: "Comic Sans MS", "Arial Rounded MT Bold", sans-serif;
}

.inner h3 {
  margin-bottom: 10px;
  font-size: 24px;
  color: #ff69b4;
}

.inner p {
  font-size: 16px;
  color: #555;
  margin-bottom: 20px;
}

.inner button {
  background-color: #ffb6c1;
  color: white;
  border: none;
  padding: 10px 20px;
  font-weight: bold;
  border-radius: 12px;
  cursor: pointer;
  transition: background-color 0.2s;
}

.inner button:hover {
  background-color: #ff69b4;
}

/* 애니메이션 */
@keyframes fadeIn {
  from {
    background-color: rgba(0, 0, 0, 0);
  }
  to {
    background-color: rgba(0, 0, 0, 0.4);
  }
}

@keyframes popUp {
  from {
    transform: scale(0.7);
    opacity: 0;
  }
  to {
    transform: scale(1);
    opacity: 1;
  }
}
</style>
