<template>
  <div id="app">
    <h1>Jogo da Forca WDEV</h1>
    <section id="inicio" v-if="tela == 'inicio'">
      Início
      <Formulario v-if="etapa == 'palavra'" title="Defina a palavra" button="Próximo" :action="setPalavra" />
      <Formulario v-if="etapa == 'dica'" title="Defina a dica" button="Iniciar Jogo" :action="setDica" />
    </section>
    <section id="jogo" v-if="tela == 'jogo'">
      Jogo
      <Jogo 
      :erros="errors"
      :palavra="palavra"
      :dica="dica"

       />
    </section>
  </div>
</template>

<script>
import './css/global.css';

import Formulario from './components/Formulario.vue';
import Jogo from './components/Jogo.vue'


export default {
  name: 'App',

  data() {
    return {
      tela: 'inicio',
      etapa: 'palavra',
      palavra: '',
      dica: '',
      errors: 0
    }
  },
  components: {
    Formulario,
    Jogo
  },
  methods: {
    setPalavra: function (palavra) {
      this.palavra = palavra;
      this.etapa = 'dica';
    },
    setDica: function (dica) {
      this.dica = dica;
      this.etapa = 'jogo';
      this.tela = 'jogo';
    }
  }
}
</script>

<style>
#app {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>
