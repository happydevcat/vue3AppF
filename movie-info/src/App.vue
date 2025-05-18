<template>
  <div>
  <Navbar />
  <SearchBar :movieData="copyMovieData" @searchMovie="searchMovie($event)"/>
  <button @click="showAllMobie">전체보기</button>
  <Modal :movieData="movieData" :isModal="isModal" :selectMovie="selectMovie" @closeModal="isModal=false"/>
  <Event  :text="text[eventTextIndex]"/>
  <h1>영화정보 </h1>
  <Movies :movieData="copyMovieData" 
  @openModal="isModal=true; selectMovie=$event"
  @increseLike="increseLike($event)"
  />
</div>

  


</template>

<script>

  import movieData from './assets/movies';
  import NavbarComponent from './components/NavbarComponent.vue';
  import ModalComponent from './components/ModalComponent.vue';
  import MovieComponent from './components/MovieComponent.vue';
  import EventComponent from './components/EventComponent.vue';
  import SearchBar from './components/SearchBar.vue';
  console.log(movieData);

  export default{
    name : 'App',
    data(){
      return {
        isModal: false,
        movieData: movieData, //원본
        copyMovieData:[...movieData], // 구조분해 사본 
        selectMovie: 0,
        text: ["NEPLIX 재미있어 !!!!!!"
              ,"쿠팡플레이!"
              ,"디지니!!!!"
              ,"HBO 젬나지"
              ],
        eventTextIndex:0,    
        interval: null,  
      }

    },

    methods: {
      increseLike(index){
        //this.movieData[index].like +=1;
        this.movieData.find(movie => {
            if(movie.id == index){
              movie.like +=1;
            }

        })
      },
      searchMovie(serchTitle){
        this.copyMovieData  = this.movieData.filter(movie =>{
          return movie.title.includes(serchTitle);
        })
      },
      showAllMobie(){
        this.copyMovieData = [...movieData];

      }
      
    },

    components:{
      Navbar: NavbarComponent,
      Event: EventComponent,
      Modal: ModalComponent,
      Movies: MovieComponent,
      SearchBar: SearchBar,
      
    } ,
    mounted() {
      console.log('mounted')     
      this.interval = setInterval(()=>{
        if(this.eventTextIndex == this.text.length-1){
          this.eventTextIndex =0;
        }else{
        this.eventTextIndex +=1;
        }
      },3000); 
    },

    unmounted() {
      console.log('unmounted');     
      clearInterval(this.interval);

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
