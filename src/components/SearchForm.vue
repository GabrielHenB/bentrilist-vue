<template>
    <div class="absolute z-100 p-16 mx-auto bg-violet-600 rounded text-light container-search">
        <form @submit.prevent="handleSearch" action="#">
            <input type="text" name="query" v-model="query" placeholder="Titulo" />
            <button class="ml-4 border border-dark bg-dark rounded p-1" type="submit">Ir</button>
            <button class="ml-1 border border-dark bg-dark rounded p-1" type="button" @click="closeSearch">Sair</button>
        </form>
    </div>
</template>

<script setup>
import {ref} from 'vue';

const query = ref("");
function handleSearch(){
    alert("Ainda não implementado teste!");
}

function closeSearch(e)
{
    //e.target.parentElement.parentElement.style = 'display: none';
    console.log("Ainda nao implementado isso");
}
</script>

<style scoped>
.container-search{
    z-index: 100;
    top: 20px;
    left: 40%;
}
</style>