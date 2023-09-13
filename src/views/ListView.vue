<template>
    <nav class="mx-2 mt-1 rounded flex justify-around align-center list-menu">
        <a href="">Criar</a>
        <a  href="#">Inserir</a>
        <a @click="isSearch = !isSearch" href="#">Pesquisar</a>
        <a @click="exportarLista" href="#">Exportar</a>
        <a @click="getJsonList" href="#">Importar</a>
        <a @click="salvarLista" href="#">Salvar</a>
        <a href="#">Destruir</a>
    </nav>
    <SearchForm v-if="isSearch" />
    <section class="my-1 mx-2 px-40 list-main">
        <table style="width: 100%" class="mx-auto table-auto tabela">
            <thead>
                <tr>
                    <th>#</th>
                    <th>Thumb</th>
                    <th>Titulo</th>
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
                    <td><button @click="editEntry" class="list-btn">edit</button><button @click="removeEntry(index, item.id, $event)" class="ml-2 list-btn">remove</button></td>
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
import {ref,computed,onMounted, nextTick} from 'vue';
import {onBeforeRouteLeave} from 'vue-router';
import ListAddForm from '../components/ListAddForm.vue';
import SearchForm from '../components/SearchForm.vue';

// ============ REFERENCIAS REATIVAS
const renderForm = ref(false);
const isSearch = ref(false);
const newone = ref({
    id: '',
    thumb: '',
    title: '',
    caps: '',
    last: '',
    completed: false
});
const list = ref([]);

// ============= LIFECYCLE HOOKS
onMounted(() => {
    const fromLocal = localStorage.getItem("userList");
    if(fromLocal){
        list.value = JSON.parse(fromLocal);
    }else{
        console.log("Erro na obtençao de dados durante montagem: Dados invalidos!");
    }
});
onBeforeRouteLeave((to,from) => {
    console.log("Salvando lista...");
    salvarLista();
    //next();
});
// ================== COMPUTED PROPERTIES
const getCompleted = computed(() => {
    //So se nao estiver completo
    return list.filter((item) => {
        return !item.completed;
    });
});

// ================== METHODS
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

function exportarLista()
{
    const jsonList = JSON.stringify(list.value);
    const blob = new Blob([jsonList], {type: "application/json"});
    const down_url = URL.createObjectURL(blob);

    const down_link = document.createElement('a');
    down_link.href = down_url;
    down_link.download = 'yourbentrilist.json';
    down_link.click(); //aciona download

    URL.revokeObjectURL(down_url);
}

function salvarLista()
{
    const jsonList = JSON.stringify(list.value);
    localStorage.setItem("userList", jsonList);
}

function editEntry(event)
{
    window.alert("Metodo ainda não implementado!");
}

function removeEntry(index, id, event)
{
    for(let ind in list.value){
        if(list.value[ind].id === id){
            if(window.confirm("Tem certeza que quer deletar?")){
                list.value.splice(ind,1); //Eh reativo??
                console.log("Indice removido!");
                return true;
            }
            else{
                return false;
            }
        }
    }
    console.log("Nao encontrado!");
    return false;
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
.list-btn{
    color: #8045E6;
}
.list-btn:hover{
    color: #f1e724;
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