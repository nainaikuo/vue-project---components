<script setup>
import { ref  , onMounted , computed} from 'vue';
// import Button  from './Button.vue'

import Form from './Form.vue';
import NoteList from './NoteList.vue'
const title = ref("fdsf")
const content = ref("")
let id = 0
const notes = ref([
    {
    id:id++,
    title:"TITLE",
    content:"CONTENT",
    priority:1
    },{
    id:id++,
    title:"TITLE",
    content:"CONTENT",
    priority:2
    },{
    id:id++,
    title:"TITLE",
    content:"CONTENT",
    priority:3
    }
])

const addNote = ()=>{
    notes.value.push(
        {
            title:title.value,
            content:content.value
        })
}

</script>

<template>
    {{ notes }}
    <div class="wrap">
        <div class="container">
            <h1>TODOLIST</h1>
            <Form 
            v-model:title="title"
            v-model:content="content"
            @addNote = "addNote"
            ></Form>
            <NoteList :data="notes" />
        
        </div>
        
 
    
    </div>
    

</template>
   


<style scoped>
h1{
    margin: 0;
    padding: 0;
}
.wrap{
    height: calc(100vh - 16px);
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 64px;
    font-family: Arial, Helvetica, sans-serif;
}
.container{
    background: #FAFAFA;
    display: flex;
    flex-direction: column;
    gap: 24px;
    padding: 32px;
    border-radius: 32px;
    width: 600px;
    box-shadow: 0 0 5px #555;
    height: fit-content;
    transition: 500ms;
    border: 1px solid #000;

}

.note--form{
    display: flex;
    flex-direction: column;
    gap:16px;
}

.note--form>.input{
    display: flex;
    flex-direction: column;
    gap: 4px;
}
.note--form label{
    font-size: 0.875rem;
    color: #333;
}

.priority-select{
    display: flex;
    width: 100%;
    gap: 8px;
}
.priority-select>button{
    flex: 1;
}

.add-note--btn{
    background: lightblue;
    font-size: 1.2rem;
    font-weight: 800;
}

.add-note--btn:hover{
    background: rgb(149, 192, 206);
}

.message{
    color: #333;
    font-size: 0.875rem;
    text-align: center;
}
.actions{
    display: flex;
    gap: 8px;
}
.actions>button{
    flex: 1;
    padding: 4px;
}

.cards{
    display: flex;
    flex-direction: column;
    gap: 16px;
}
.card{
    /* background: #000; */

    padding: 16px;
    border-radius: 16px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    min-height: 80px;
    animation: moveIn 500ms ease-in-out;
}

@keyframes moveIn {
    from{
        opacity: 0;
        transform: translateX(-100px);
    }
    to{
        opacity: 1;
        transform: translateX(0);
    }
    
}

.card--action{
    /* border: 1px solid #000; */
    display: flex;
    gap: 8px;
}
.card--action>button{
    padding: 4px 8px;
    font-size: 0.75rem;
    background: #FFF;
}

.card.red{
    background: #ecc4c4;
}
.card.green{
    background: #caeeca;
}

.card.blue{
    background: #b3cafd;
}

.card.done{
    background: #EEE;
}
.card.done h3,.card.done p{
    text-decoration: line-through;
}






</style>