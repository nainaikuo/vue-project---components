
<script setup>

import {ref} from 'vue'
defineProps(["value","color","type","size"])

</script>

<template>

<button :class="[color,type,size]" :value="value" >
    <slot></slot>
</button>

</template>

<style scoped>
*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
button{
    padding: 8px 16px;
    border-radius: 8px;
    cursor: pointer;
}

button.small{
    padding: 4px 8px;
    font-size: 0.8rem;
}
button.outline{
    background: none;
    border: 1px solid #333;
    color: #333;
}
button.text{
    background: none;
    border: none;
    border-radius: 0px;
    color: #333;
}
button.text:hover{
    box-shadow: 0 1px 0 #333;
}


.primary.filled{
    background: rgb(120, 209, 209);
    color: #FFF;
    border: 1px solid rgb(120, 209, 209);
}
.primary.filled:hover{
    background: rgb(103, 180, 180);

}
.primary.outline{
    border: 1px solid rgb(120, 209, 209);
    background: none;
    color: rgb(120, 209, 209);

}
.primary.outline:hover{
    background: rgb(120, 209, 209);
    color: #FFF;

}
.primary.text{

    color: rgb(120, 209, 209);

}
.primary.text:hover{
    box-shadow: 0 1px 0 rgb(120, 209, 209);
}

</style>