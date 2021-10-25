<template>
    <div class="col">
        <a href="#"><img class="img-fluid" :src="require('../assets/' + imagem + '.jpg')" :alt="`${nome}`"></a>
        <h4 class="text-center">{{ nome }}</h4>
    </div>
</template>
<script>
export default {
    name: "Produto",
    props: {
        id: Number,
        nome: String,
        imagem: String
    },
    methods: {}
}
</script>

<style scoped></style>
