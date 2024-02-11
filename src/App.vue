<script setup>
import { ref  , onMounted , computed} from 'vue';
// import Button  from './Button.vue'

import Form from './Form.vue';
import NoteList from './NoteList.vue'
const title = ref("")
const content = ref("")
const priority =ref(1)
let id = 0
const notes = ref([
    {
    id:id++,
    title:"TITLE",
    content:"CONTENT",
    priority:1,
    isDone:false,
    }
])

const addNote = (priorityValue)=>{
    notes.value.unshift(
        {   id:id++,
            title:title.value,
            content:content.value,
            priority:priorityValue
        })
        title.value=""
        content.value=""
        priority.value=null
}



const finNote = (id)=>{
    const selectNote = notes.value.find(i=>i.id===id)
    selectNote.isDone = !selectNote.isDone
}
const delNote = (id)=>{
    notes.value = notes.value.filter(note=>note.id !== id)
}


</script>

<template>

    <div class="wrap">
        <div class="container">
            
    {{ title}}
    {{ content }}
    APP:{{ priority }}
            <h1>TODOLIST</h1>
            <Form 
            v-model:title="title"
            v-model:content="content"
            v-model:priority="priority"
            @addNote = "addNote"
            ></Form>
            <NoteList 
            @delNote = "delNote" 
            @finNote = "finNote"
            :data="notes" />
        
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

}



</style>