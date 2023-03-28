<script>
export default {
    data() {
        return {
            lista: []
        }
    },
    created(){
        this.trocar()
    },
    methods: {
        trocar(){
            fetch("https://jsonplaceholder.typicode.com/posts")
            .then(e=>e.json())
            .then(e=>{
                console.log(e)
                this.lista = e
            })
        }
    },
}
</script>

<template>
    <section class="my-3 p-3 bg-body rounded shadow-sm">
        <h6 class="border-bottom pb-2 mb-0"><strong>POSTS</strong></h6>
        <div class="border-bottom py-3" v-for="item in lista" v-bind:key="item">
            <strong>{{ item.title }}</strong>
            <p class="m-0">{{ item.body }}</p>
        </div>
    </section>
</template>

<style scoped>
    @import url("https://unpkg.com/leaflet@1.9.3/dist/leaflet.css")
</style>
