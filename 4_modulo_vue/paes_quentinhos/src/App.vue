<template>
    <div id="app">
        <h1 class="text-center">Sejam bem vindos à Padaria Online do Sr. Bertti</h1>
        <div class="container" id="products">
            <div class="row" v-for="(prods, idx) in grid" :key="idx">
                <Produto v-for="p in prods"
                    :key="p.id"
                    :id="p.id"
                    :nome="p.nome"
                    :imagem="p.id_imagem"
                />
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
import Produto from "@/components/Produto";

export default {
    name: 'App',
    components: {
        Produto
    },
    data() {
        return {
            grid: []
        }
    },
    beforeMount() {
        axios
            .get("https://raw.githubusercontent.com/jpedrojpedro/simple-front/master/static/menu.json")
            .then(response => {
                let produtos = response.data.produtos
                let tamGrid = 3
                for(let index = 0; index < produtos.length; index += tamGrid) {
                    let gridProd = produtos.slice(index, index + tamGrid);
                    this.grid.push(gridProd);
                }
            })
    }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
