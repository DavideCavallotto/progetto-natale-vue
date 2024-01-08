
<script setup>
import axios from 'axios';
import { ref, onMounted } from 'vue'



let pokedex = ref(null)



onMounted(() => {
    console.log(axios)

    axios.get('https://pokeapi.co/api/v2/pokemon')
        .then(function (res) {

            pokedex.value = res.data.results
            console.log(res)
        })
})



</script>

<template>
    <div>
        <h1>Pokedex</h1>
        <div class="container">
            <div class="row">
                <div class="col-3" v-for="pokemon in pokedex">
                    <div class="card" style="width: 18rem;">
                        <img :src="pokemon.url" class="card-img-top" alt="">
                        <div class="card-body">
                            <h5 class="card-title">{{pokemon.name}}</h5>
                            
                        </div>
                    </div>

                </div>
            </div>

        </div>

        
    </div>
</template>

<style></style>