<template>
    <div class="corpo">
        <router-view></router-view>
        <nav>
            <ul>
                <li v-for="route in routes" :key="route">
                    <router-link :to="route.path ? route.path : '/'"> 
                        {{ route.titulo }} 
                    </router-link>
                </li>
            </ul>
        </nav>
    </div>
</template>

<script>
    import { routes } from './routes'

    export default {
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

</style>
