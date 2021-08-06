<template>
  <h1>Tiempo de reacción</h1>
  <button @click="iniciarJuego" :disabled="jugando">Jugar</button>
  <Block v-if="jugando" :delay="delay" @finalizar="TerminarJuego"/>

 <Results v-if="mostrarResultados"  :puntaje="puntaje" />
</template>

<script>

import Block from './components/Block.vue'
import Results from './components/Results.vue'


export default {
  name: 'App',
  components: { Block , Results },
  data(){
    return {
      jugando:false,
      delay: null,
      puntaje: null,
      mostrarResultados:false
    }
  },
  methods: {
    iniciarJuego() {
      this.delay = 2000 + Math.random() * 5000
      this.jugando = true,
      this.mostrarResultados = false
      console.log(this.delay)


    },
    TerminarJuego(tiempoReaccion){
        this.puntaje = tiempoReaccion,
        this.jugando = false,
        this.mostrarResultados = true
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
button{
  background: #0faf87;
  color: white;
  border:none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled]{
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
