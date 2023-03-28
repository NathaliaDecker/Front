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
            fetch("https://jsonplaceholder.typicode.com/posts/4/comments")
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
        <h6 class="border-bottom pb-2 mb-0"><strong>POSTS ID</strong></h6>
        <div class="border-bottom py-3" v-for="item in lista" v-bind:key="item">
            <p class="m-0">Name: {{ item.name }}</p>
            <p class="m-0">Email: {{ item.email }}</p>
            <p class="m-0">Body: {{ item.body }}</p>
        </div>
    </section>
</template>

<style scoped>
    
</style>
