<template>
  <div id="app">
    <h1>Jogo da Forca WDEV</h1>
    <section id="inicio" v-if="tela == 'inicio'">
      <Formulario v-if="etapa == 'palavra'" title="Defina a palavra" button="Próximo" :action="setPalavra" />
      <Formulario v-if="etapa == 'dica'" title="Defina a dica" button="Iniciar Jogo" :action="setDica" />
    </section>
    <section id="jogo" v-if="tela == 'jogo'">
      <Jogo :erros="errors" :palavra="palavra" :dica="dica" :verificaLetra="verificaLetra" :etapa="etapa" :letras="letras"
        :jogar="jogar" :jogarNovamente="jogarNovamente" />
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
      errors: 0,
      letras: [],
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
    },
    verificaLetra: function (letra) {
      return this?.letras?.find(item => item.toLowerCase() === letra.toLowerCase());
    },
    jogar: function (letra) {
      this.letras.push(letra);
      //validar erro
      this.verificarErros(letra)
    },
    verificarErros: function (letra) {
      if (this.palavra.toLocaleLowerCase().indexOf(letra.toLocaleLowerCase()) >= 0) {
        return this.verificarAcertos();
      }
      this.errors++;
      if (this.errors === 6) {
        this.etapa = 'enforcado';
      }
    },
    verificarAcertos: function () {
      //pega as letras sem repetir
      let letrasUnicas = [...new Set(this.palavra.split(''))];
      if (letrasUnicas.length === (this.letras.length - this.errors)) {
        this.etapa = "ganhador"
      }
    },
    jogarNovamente: function () {
      this.palavra = '';
      this.dica = '';
      this.erros = 0;
      this.letras = [];
      this.tela = 'inicio';
      this.etapa = 'palavra';
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
