<template>
    <div class="corpo">
        <meu-menu :rotas="routes" :key="routes"/>
        
        <transition name="pagina">
            <router-view></router-view>
        </transition> 


    </div>
</template>

<script>
    import Menu from './components/shared/menu/Menu.vue';
    import { routes } from './routes';

    


    export default {
        components: {
        'meu-menu': Menu
        },
        data () {
            return {
                routes
            }
        }
    }

</script>

<style>
    .corpo {
        font-family: Helvetica, sans-serif;
        width: 98%;
        margin: 0 auto;
    }

    .pagina-enter-active, .pagina-leave-active {
        transition: opacity 3s;
    }

    .pagina-enter, .pagina-leave-active {
        opacity: 0;
    }

</style>
