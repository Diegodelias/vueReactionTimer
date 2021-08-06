<template>
<p>Tiempo de reaccion {{  puntaje }} ms</p>
<p class="rank">{{ rank }}</p>
</template>

<script>
export default {
  props: ['puntaje'],
  data(){
      return {
          rank: null
      }
  },
  mounted() {
      if (this.puntaje < 500){
          this.rank = "Excelente puntaje"

      } else if(this.puntaje < 800) {
          this.rank = "Puntaje medio"
      } else {
          this.rank ="Puntaje bajo"
      }
  }
}
</script>

<style>

.rank {
    font-size: 1.4em;
    color: #0faf87;
    font-weight:bold;
}


</style>