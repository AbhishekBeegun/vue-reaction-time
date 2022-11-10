<template>
  <div class="result">
    <p>Reaction Time {{ score }} milliseconds</p>
    <p class="rank">{{rank}}</p>  
  </div>
</template>

<script>
export default {
    props:['score'],
    data(){
      return{
        rank:null
      }
    },

    mounted(){
      if(this.score < 250){
        this.rank = "Thats very quick"
      } else if (this.score < 400){
        this.rank = "You can do better"
      } else {
        this.rank = 'Really Come On!!do better'
      }
    }

}
</script>

<style>
.result{
    width: 800px;
    border-radius: 20px;
    background: red;
    color:white;
    font-size:2rem;
    text-align: center;
    padding: 100px 0;
    margin:40px auto;
}

.result p{
  background-color: red;
}

.rank {
  font-size: 1.5rem;

}

</style>