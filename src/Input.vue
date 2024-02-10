<script setup>
import {ref} from 'vue'
defineProps(["id","label","type","placeholder"])
</script>

<template>

<div class="input">
    <label :for="id">{{ label }}</label>
    <input :type="type" :id="id" :placeholder="placeholder">
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

</style>