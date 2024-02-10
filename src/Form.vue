<script setup>
import {ref} from 'vue'

import Input from './Input.vue';
import Button from './Button.vue';
const title = defineModel("title")
const content = defineModel("content")
</script>

<template>
<div class="form-wrap">
    <div class="input">
    <label for="title">標題</label>
    <input  type="text" v-model="title" id="title" placeholder="輸入標題">
</div>
<div class="input">
    <label for="content">內容</label>
    <input type="text" v-model="content" id="content" placeholder="輸入內容">
</div>
    <div class="form--actions">
        <Button  text="清除" color="primary" type="outline"/>
        <Button @click="$emit('addNote')" text="新增" color="primary" type="filled"/>
    
    </div>
    
</div>

</template>

<style scoped>


.input{
    display: flex;
    flex-direction: column;
    gap: 4px;
}
label{
    color: #333;
    font-size: 0.857rem;
}
input{
    padding: 8px;
    border-radius: 4px;
    border: 1px solid #CCC;
    color: #333;
    flex: 1;
}
input:focus{
    outline:0.5px solid #555;
}
.form-wrap{
    display: flex;
    flex-direction: column;
    gap:16px;
}
.form--actions{
    display: flex;
    gap: 8px;
}
.form--actions>Button{
    flex: 1;
}

</style>