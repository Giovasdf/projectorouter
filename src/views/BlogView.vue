<template>
    <div>
        <h1>{{ tituloEntrada }}</h1>
        <router-link :to="paginar(false)">Anterior</router-link>
        <router-link :to="paginar(true)">Siguiente</router-link>
        <br>
        <button @click="volverInicio" class="button-index">Volver al inicio</button>
    </div>
</template>

<script>
export default {
    name: 'BlogView',
    methods: {
        paginar(siguiente) {
            let entrada = parseInt(this.$route.params.entrada)
            if (siguiente) {
                return entrada < 10 ? `/blog/${entrada+1}` : `/blog/${entrada}`
            } else {
                return entrada > 1 ? `/blog/${entrada-1}` : `/blog/${entrada}`
            }
        },
        volverInicio() {
            return this.$router.push('/')
        }
    },
    computed: {
        tituloEntrada() {
            return `Entrada ${this.$route.params.entrada} del Blog`
        }
    }
}

</script>

<style scoped>
.button-index {
    margin-top: 10px;
    padding: 5px;
    color: white;
    background-color: #43b983;
}
</style>
