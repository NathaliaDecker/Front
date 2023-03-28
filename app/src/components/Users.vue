<script>
export default {

    data() {
        return {
            lista: [],
            
        }
    },
    created(){
        this.trocar()
    },
    methods: {

        clicado(val) {
            this.$emit('botaoClicado' , val);
            // console.log('botaoclicado')
        },

        trocar(){
            fetch("https://jsonplaceholder.typicode.com/users")
            .then(e=>e.json())
            .then(e=>{
                console.log(e)
                this.lista = e
            })
        },
        
        
    },
}
</script>


<!-- maps -->



<template>
    <section class="my-3 p-3 bg-body rounded shadow-sm">
        <h6 class="border-bottom pb-2 mb-0"><strong>USERS</strong></h6>
        <div class="border-bottom py-3" v-for="item in lista" v-bind:key="item">
            <p class="m-0"><b>name: </b> {{ item.name }}</p>
            <p class="m-0"><b>email: </b> {{ item.email }}</p>
            <p class="m-0"><b>phone: </b> {{ item.phone }}</p>
            <p class="m-0"><b>username: </b> {{ item.username }}</p>
            <p class="m-0"><b>website: </b> {{ item.website }}</p>
            <button @click="clicado(item.id)" class="btn btn-sm btn-outline-secondary mt-2">See all informations</button>
        </div>
    </section>
</template>

<style scoped>
    @import url("https://unpkg.com/leaflet@1.9.3/dist/leaflet.css")
</style>
