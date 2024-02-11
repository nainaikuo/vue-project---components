<script setup>
import { ref } from 'vue'

import Input from './Input.vue';
import Button from './Button.vue';
import Select from './Select.vue';
const title = defineModel("title")
const content = defineModel("content")
const priority = defineModel("priority")
let priorityText = ref()


const prioritySet = ref([
    {
        text: "緊急",
        value: 3
    },
    {
        text: "優先",
        value: 2
    }, {
        text: "普通",
        value: 1
    }
])

const init = () => {
    
    if (!priority.value) {
        priorityText = ref(null)
    } else {
        const text = prioritySet.value.find(i => i.value === priority.value).text
        priorityText = ref(text)
    }

}




const clearInput = () => {
    title.value = ""
    content.value = ""
    priority.value = null
    priorityText = null
}
init()

</script>

<template>
    <div class="form-wrap">
        <div class="input">
            <label for="title">標題</label>
            <input type="text" v-model="title" id="title" placeholder="輸入標題">
        </div>
        <div class="input">
            <label for="content">內容</label>
            <input type="text" v-model="content" id="content" placeholder="輸入內容">
        </div>
        FORM:{{ priority }}{{ priorityText }}
        <Select initialValue="選擇優先度" :options="prioritySet" v-model:value="priority"
            v-model:text="priorityText">優先度</Select>
        <div class="form--actions">
            <Button @click="clearInput" text="清除" color="primary" type="outline">清除</Button>
            <Button @click="$emit('addNote', priority)" text="新增" color="primary" type="filled">新增</Button>

        </div>

    </div>
</template>

<style scoped>
.input {
    display: flex;
    flex-direction: column;
    gap: 4px;
}

label {
    color: #333;
    font-size: 0.857rem;
}

input {
    padding: 8px;
    border-radius: 4px;
    border: 1px solid #CCC;
    color: #333;
    flex: 1;
}

input:focus {
    outline: 0.5px solid #555;
}

input::placeholder {
    color: #555;
    font-size: 0.8rem;
}

.form-wrap {
    display: flex;
    flex-direction: column;
    gap: 16px;
}

.form--actions {
    display: flex;
    gap: 8px;
}

.form--actions>Button {
    flex: 1;
}
</style>