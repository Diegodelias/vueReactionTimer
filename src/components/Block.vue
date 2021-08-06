<template>
<div class="block" v-if="mostrarCuadrado" @click="detenerTimer">
    cliquear acá
</div>
  
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            mostrarCuadrado: false,
            timer: null,
            TiempoReaccion:0
        }
    },

    mounted() {
        
        setTimeout(() => {

            this.mostrarCuadrado = true
            this.iniciarTimer()


        }, this.delay)
    },
  methods:{
      iniciarTimer() {
          this.timer = setInterval(() => {
              this.TiempoReaccion += 10

          }, 10)

      },
      detenerTimer() {
          clearInterval(this.timer)
          console.log(this.TiempoReaccion)
          this.$emit('finalizar', this.TiempoReaccion)


      }
  }
   

}
</script>

<style>
.block {
    width: 400px;
    border-radius: 20px;
    background: #0faf87;
    color:#fff;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}

</style>