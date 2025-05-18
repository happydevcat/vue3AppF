<template>
  <div>
    <p>SerchBar :: {{ inputText }}</p>
    <div class="search-box">
      <input type="search" @change="$emit(`searchMovie`,$event.target.value); inputText= $event.target.value;"> <!-- v-model="inputText" == @input="inputText= $event.target.value"-->
      <button>Search</button>
    </div>
  </div>
</template>

<script>
export default {
  name:"SearchBar",
  props:{
    movieData: Array,
  },
  data(){
    return{
      inputText:'',
    }
  },
  watch:{
    inputText(inputVal) {
      // 입력한 영화제목이 데이터에 있는지 확인해보자
      // if(inputVal !=="노랑"){
      //   alert('왜');
      // }
      const findMovie = this.movieData.filter(movie =>{
        return movie.title.includes(inputVal);
        
      })
      console.log(findMovie);
      if(findMovie.length == 0){

        alert('존재하지 않는 영화입니다.');
      }

    }
  }
}
</script>

<style  scoped>

</style>