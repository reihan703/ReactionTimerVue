<template>
  <div class="results">
      <h3>Your Score: {{score}}</h3>
      <p class="rank">{{rank}}</p>
  </div>
</template>

<script>
export default {
    props:['score'],
    data(){
        return{
            rank:null,
        }
    },
    mounted(){
        if(this.score<=250){
            this.rank='Fast'
        }
        else if(this.score<400){
            this.rank='ok'
        }
        else{
            this.rank='got a hand?'
        }
    }
}
</script>

<style>
    .rank{
        font-weight: bold;
    }
</style>