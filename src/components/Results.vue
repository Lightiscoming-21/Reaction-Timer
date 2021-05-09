<template>
  <p>reaction time = {{score}} ms</p>
  <p class="rank">{{rank}}</p>
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
        if(this.score<250){
            this.rank = 'ninja fingers'
        }
        else if(this.score<400){
            this.rank = 'rapid reflexes'
        }
        else{
            this.rank = 'snail pace...'
        }

    }

}
</script>

<style>
.rank{
    font-size: 1.4em;
    color: blue;
    font-weight: bold;
}
</style>