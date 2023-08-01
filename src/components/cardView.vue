<script setup>
defineProps({
    title: String,
    author: String,
    year: Number,
    body: {
        type : String,
        default: " La API permite buscar libros utilizando diversos criterios, como título, autor, género o palabras clave. Los resultados de la búsqueda se devuelven en formato JSON u otro formato estándar, lo que facilita la integración con aplicaciones y servicios de terceros.",
    }

})
const emit = defineEmits(['añadirFavorito'])
</script>

<template>
    <div class="col">
        <div class="card">
            <div class="card-body">
                    <h5 class="card-title">{{title}} - {{ author }} - {{ year }} </h5>
                        <p class="card-text">{{body}}</p>
                        <div class="d-grid">
                        </div>
                    </div>
                </div>    
        </div>
</template>