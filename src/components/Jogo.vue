<template>
    <div class="jogo">
        <Forca :erros="erros" />
        <Palavra :palavra="palavra" :dica="dica"/>
    </div>
</template>

<script>
import Forca from './Forca.vue';
import Palavra from './Palavra';

export default {

    name: 'Jogo',
    props: {
        erros: Number,
        palavra:String,
        dica:String
    },

    data() {

    },
    methods: {

    },
    components: {
        Forca,
        Palavra,
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