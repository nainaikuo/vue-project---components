<script setup>
import {ref} from 'vue';
const props = defineProps(["initialValue","options","id"])
const value = defineModel("value")
const text  = defineModel("text")
const isOpen = ref(false)
console.log(text.value)
const selected = ref({
    text:text,
    value:value
})
console.log(selected.value.text)
const toggleSubmenu = ()=>{
    isOpen.value = !isOpen.value
}

const setValue = (value,text) =>{
    selected.value.value = value
    selected.value.text = text
    toggleSubmenu()
}

</script>




<template>
    <div class="select-wrap">
        <label for=""><slot></slot></label>
        <div class="selector" >
        <div class="select"  @click="toggleSubmenu">
            {{ selected.text?selected.text:initialValue }}
        </div>
        <ul class="sub-menu" :class="{'open':isOpen}">
            <li 
            class="sub-menu--item" 
            @click="setValue(option.value,option.text)"
            v-for="option in options" >{{ option.text }}</li>
        </ul>
        </div>
         
    </div>
    
</template>

<style scoped>

*{
    box-sizing: border-box;
}
.select-wrap{
    position: relative;
    cursor: pointer;
    display: flex;
    flex-direction: column;
    gap:4px;
}
label{
    color: #333;
    font-size: 0.857rem;
}
.selector{
    position: relative;
}
.select{
    padding: 8px;
    border-radius: 4px;
    border: 1px solid #CCC;
    background: #FFF;
    color: #555;
    margin: 0;
    font-size: 0.8rem;
    position: relative;
    min-height: 36px;
}
.select.has-value{
    color: #333;
}
.select::after{
    content:"三角形";
    position: absolute;
    height: 100%;
    right: 8px;
    top: 0;
    display: flex;
    align-items: center;
    justify-content: center;
}
.sub-menu{
    box-sizing: border-box;
    background: rgba(255,255,255);
    padding: 0;
    margin: 0;
    list-style:none;  
    border-radius: 4px;
    width: 100%;
    position: absolute;
    overflow: hidden;
    max-height: 0;
    border: 0px solid #CCC;
    transition:0ms;
}

.sub-menu.open{
    max-height: calc(36px *4 );
    border: 1px solid #CCC;
    overflow-y: scroll;
    scroll-behavior: smooth;
    transition: 300ms;
}
.sub-menu::-webkit-scrollbar{
    display: none;
}
.sub-menu--item{
    padding: 8px;
    border-bottom: 1px solid #ccc;
    font-size: 0.875rem;
min-height: 36px;
    
}

.sub-menu--item:hover{
    background: rgb(120, 209, 209,0.2);
}
</style>