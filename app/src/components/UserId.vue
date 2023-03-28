<script>


export default {

    props: {
        num: {
            type: Number,
            default: 2
        }
    },

    data() {
        return {
            info: {},
            address:{},
            num: this.num,
            numero: 1
        }
    },

    watch: {
        num(novo, velho){
            this.map_start()
            this.num = novo
        }
    },

    created(){
        this.map_start()
    },

    methods: {

        go(){
    
            fetch("https://jsonplaceholder.typicode.com/users/"+this.num)
            .then(e=>e.json())
            .then(e=>{
                L.marker([e.address.geo.lat, e.address.geo.lng]).addTo(this.map);
            })
            
        },
        
        map_start(){   
            fetch("https://jsonplaceholder.typicode.com/users/"+this.num)
            .then(e=>e.json())
            .then(e=>{

                this.info = e
                this.address = e.address

                // let map = L.map('map').setView([e.address.geo.lat, e.address.geo.lng], 13)
                this.map = L.map('map').setView([e.address.geo.lat, e.address.geo.lng], 13)

                L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
                    maxZoom: 20,
                    attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
                }).addTo(this.map);

                L.marker([e.address.geo.lat, e.address.geo.lng]).addTo(this.map);

            })
        }
    },
}


</script>


<template>


    <section class="my-3 p-3 bg-body rounded shadow-sm">
        <h6 class="border-bottom pb-2 mb-0"><strong>USER ID</strong></h6>
        <div class="border-bottom py-3">
            
            <h2>Info {{ num }} </h2>
            <p class="m-0">Name: {{ info.name }}</p>
            <p class="m-0">username: {{ info.username }}</p>
            <p class="m-0">email: {{ info.email }}</p>
            <p class="m-0">phone: {{ info.phone }}</p>
            <p class="m-0">website: {{ info.website }}</p>

            <h2 class="mt-3">Adress</h2>
            <p class="m-0">city: {{ address.city }}</p>
            <p class="m-0">street: {{ address.street }}</p>
            <p class="m-0">suite: {{ address.suite }}</p>
            <p class="m-0">zipcode: {{ address.zipcode }}</p>

            <div id="map" class="my-3"></div>

        </div>
    </section>
</template>


<style scoped>
    #map { height: 380px; }
</style>
