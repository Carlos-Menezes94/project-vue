<template>
    <div class="corpo">
        <h1 class="centralizado">{{ titulo }}</h1>

        <ul class="lista-fotos">
            <li class="lista-fotos-item" v-for="foto of fotos" :key="foto.titulo">
                <img :src="foto.url" :alt="foto.titulo">
            </li>
        </ul>


    </div>
</template>

<script>
export default {

    data() {
        return {
            titulo: 'Arrombadineos',
            fotos: []
        }
    }, 
        
created() {
    this.$http.get('http://localhost:3000/v1/fotos')
        .then(res=> res.json())
        .then(fotos => this.fotos = fotos, err => console.log(err));
    }

}
</script>

<style>

</style>
