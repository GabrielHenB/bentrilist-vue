<template>
    <nav class="mx-2 mt-1 rounded flex justify-around align-center list-menu">
        <a href="">Criar</a>
        <a href="">Inserir</a>
        <a href="">Pesquisar</a>
        <a href="">Exportar</a>
        <a @click="getJsonList" href="#">Importar</a>
        <a @click="salvarLista" href="#">Salvar</a>
        <a href="">Destruir</a>
    </nav>
    <section class="my-1 mx-2 px-40 list-main">
        <table style="width: 100%" class="mx-auto table-auto tabela">
            <thead>
                <tr>
                    <th>#</th>
                    <th>Thumb</th>
                    <th >Titulo</th>
                    <th>Capítulos</th>
                    <th>Ultimo</th>
                    <th>Opções</th>
                </tr>
            </thead>
            <tbody>
                <tr :id="item.id" v-for="(item,index) of list" v-bind:key="item.id" class="border">
                    <td>{{ index }}</td>
                    <td><img :src="item.thumb" width="100" alt="" /></td>
                    <td>{{ item.title }}</td>
                    <td>{{ item.caps }}</td>
                    <td>{{ item.last }}</td>
                    <td><button>edit</button><button class="ml-2">remove</button></td>
                </tr>
                <ListAddForm v-if="renderForm" v-on:send-new="receiveNew"/>
            </tbody>
        </table>
    </section>
    <div @click="startAdd" class="fixed menu-lateral">
        <img src="addbtn.png" alt="Add" width="60">
    </div>
</template>

<script setup>
import {ref,computed} from 'vue';
import ListAddForm from '../components/ListAddForm.vue';


const renderForm = ref(false);
const newone = ref({
    id: '',
    thumb: '',
    title: '',
    caps: '',
    last: '',
    completed: false
});
const list = ref([]);

function getJsonList(){
    try{
        fetch('./examples.json') // Adjust the path as needed
      .then(response => response.json())
      .then(data => {
        list.value = data;
      })
      .catch(error => {
        console.error('Erro carregando JSON data:', error);
      });
    }catch(err){
        console.log(err);
    }
}

const getCompleted = computed(() => {
    //So se nao estiver completo
    return list.filter((item) => {
        return !item.completed;
    });
});

function receiveNew(a_emit)
{
    console.log(a_emit);
    newone.value = a_emit;
    try{
        list.value.push({...newone.value});
    }catch(anyerror){
        console.log("Erro durante o processamento = " + anyerror);
    }
    renderForm.value = false;
}

function salvarLista()
{
    const jsonList = JSON.stringify(list.value);
    localStorage.setItem("userList",jsonList);
}

function startAdd()
{
    renderForm.value = true;
}
</script>

<style scoped>
.tabela{
    background-color: #202020;
    color: #FFFFFF;
}
thead{
    background-color:#6931ca;
}
tr td, tr th{
    text-align: center;
}
td{
    padding-left: 4px;
}
.list-menu{
    background-color: #8045E6;
    color: #E6DE45;
}
.menu-lateral{
    border-radius: 45%;
    background-color: #f1e724;
    color: #9014a8;
    font-size: large;
    padding: 28px;
    right: 16px;
    bottom: 16px;
    cursor: pointer;
}
</style>