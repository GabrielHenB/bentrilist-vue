<script setup>
import {onMounted,ref} from 'vue';
const emit = defineEmits(['send-new']);

const newrow = ref({
    id: '',
    thumb: '',
    title: '',
    caps: '',
    last: '',
    completed: false
});

function handle(){
    //console.log('acionado');
    //console.log(newrow.value);
    emit('send-new', newrow.value);
}

onMounted(() => {
    document.querySelector('.newrow').scrollIntoView({behavior: 'smooth'});
})

</script>
<template>
    <tr class="pb-10 newrow">
        <td><input type="number" class=" entrada" v-model="newrow.id" name="id" placeholder="ID" /></td>
        <td><input type="text" class=" entrada" v-model="newrow.thumb" name="thumb" placeholder="URL da Thumb" /></td>
        <td><input type="text" class=" entrada" v-model="newrow.title" name="title" placeholder="Titulo do Item" /></td>
        <td><input type="text" class=" entrada" v-model="newrow.caps" name="caps" placeholder="Caps/Eps"></td>
        <td><input type="text" class=" entrada" v-model="newrow.last" name="last" placeholder="Ultimo Cap/Ep"></td>
        <td><button @click="handle()">insert</button><button class="ml-2">cancel</button></td>
    </tr>
</template>

<style scoped>
.entrada{
    color: white;
    margin: 0px 2px;
    padding: 0px 2px;
    background-color: #242424;
    border: 1px solid white;
}
</style>