<template>
  <div class="corpo">
    <h1 class="centralizado">{{ titulo }}</h1>
    <input class="filtro" @input="filtro = $event.target.value" placeholder="Pesquise a foto/imagem">
        <ul class="lista-fotos">
            <li class="lista-fotos-item" v-for="foto in fotosFiltro" :key="foto.titulo">
                <meu-painel :titulo="foto.titulo">
                    <imagem-responsiva :src="foto.url" :alt="foto.titulo" />
                </meu-painel>
            </li>
        </ul>
  </div>
</template>

<script>
import ImagemResonsiva from '../shared/imagem-responsiva/ImagemResonsiva.vue';
import Painel from '../shared/painel/Painel.vue';

export default {

    components: {

        'meu-painel': Painel,
        'imagem-responsiva': ImagemResonsiva
    },

    data () {
        return {

        titulo: 'IMG IMG', 
        fotos: [],
        filtro: ''
        }
    },
        
    computed:{
        fotosFiltro(){
            if(this.filtro){
                let exp = new RegExp(this.filtro.trim(), 'i');
                return this.fotos.filter(foto => exp.test(foto.titulo));
            }else{
                return this.fotos;
            }
        }
    },

    created() {

        this.$http
        .get('http://localhost:3000/v1/fotos')
        .then(res => res.json())
        .then(fotos => this.fotos = fotos, err => console.log(err));
    }
}
</script>

<style>
.corpo {
    font-family: Helvetica, sans-serif;
    width: 98%;
    margin: 0 auto;
}

.centralizado {
    text-align: center;
}

.lista-fotos {
    list-style: none;
}

.lista-fotos .lista-fotos-item {
    display: inline-block;
}

.filtro {
    display: block;
    width: 100%;
}


</style>
