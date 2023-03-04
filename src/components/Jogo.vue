<template>
    <div class="jogo">
        <Forca :erros="erros" />
        <Palavra :palavra="palavra" :dica="dica" :verificaLetra="verificaLetra" :etapa="etapa" />
        <Teclado v-if="etapa === 'jogo'" :letras="letras" :verificaLetra="verificaLetra" :jogar="jogar" />
        <Final v-if="etapa != 'jogo'" :etapa="etapa" :texto="etapa === 'ganhador' ? 'Parabéns :)' : 'Perdeu :('"
            :jogarNovamente="jogarNovamente" />
    </div>
</template>

<script>
import Forca from './Forca.vue';
import Palavra from './Palavra.vue';
import Teclado from './Teclado.vue';
import Final from './Final.vue';

export default {

    name: 'Jogo',
    props: {
        erros: Number,
        palavra: String,
        dica: String,
        verificaLetra: Function,
        jogar: Function,
        jogarNovamente: Function,
        etapa: String,
        letras: Array
    },

    data() {

    },
    methods: {

    },
    components: {
        Forca,
        Palavra,
        Teclado,
        Final
    }
}
</script>

<style scoped>
.jogo {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
}
</style>