<template>
    <div class="palavra">

    </div>
</template>
<script>
export default {
    name: 'Palavra',
    props: {
        palavra: String,
        dica: String
    }
}
</script>

<style scoped>
.palavra {
    text-transform: uppercase;
    display: flex;
    flex-direction: column;
    text-align: center;
    align-items: center;
}

.palavra-letras {
    display: flex;
    margin-bottom: 20px;
}

.palavra-letra {
    height: 30px;
    width: 30px;
    margin: 0px 5px;
    border-bottom: 1px solid var(--color-text-light);
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>