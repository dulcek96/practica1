<script setup>
import {RouterLink, RouterView} from 'vue-router'
import Cards from './components/cardView.vue'
import LoadingSpinner from './components/icons/LoadingView.vue'

let favorito = ref('')
let posts = ref ([])
let loading = ref(true)


const añadirFavorito = (cardFavorito) => {
favorito.value = cardFavorito
}

const getData = async() => {
try {
    const res = await fetch('https://raw.githubusercontent.com/dulcek96/API/main/JSON/Book.json')
    posts.value = await res.json()
} catch (error) {
    console.log(error)
} finally{
    setTimeout (() => {
        loading.value = false
    }, 1000)
    }
}
getData()

</script>

<template>
    <LoadingSpinner v-if="loading"/>
    <div v-else>
    <h1> Mis Cards {{ favorito }}</h1>
    <div class="container"> 
    <section clas=" row row-cols-1 row-cols-md-2 g-4">
        <Cards 
        v-for="item in posts"
        :key="item.id" 
        :title="item.title"
        :author="item.author"
        :year="item.year"
        :body="item.body"
        />
        </section>
    </div>
    </div>
</template>
<style>
body{
    display: flex;
    justify-content: center;
    background: #654ea3; 
    background: -webkit-linear-gradient(to right, #eaafc8, #654ea3);  
    background: linear-gradient(to right, #eaafc8, #654ea3); 
    text-align: center;
    margin: 0;
    padding: 0;
    font-family: sans-serif;
}
h1{
    color: white;
    font-size: 40px;
}

.card {
    display: flex;
    justify-content: center;
    width: 300px;
    background-color: #f5f5f5;
    border: 1px solid #ccc;
    border-radius: 8px;
    padding: 16px;
    margin-bottom: 16px;
}

.card-title {
    font-size: 18px;
    font-weight: bold;
}

.card-text {

    font-size: 14px;
}

</style>
