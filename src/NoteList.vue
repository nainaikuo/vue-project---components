<script setup>
defineProps(["data"])
import Button from './Button.vue'
</script>

<template>
    <ul class="note-list">
        <li v-for="note in data" 
        :class="[
            {
            'primary': note.priority == 1,
            'warning': note.priority == 2,
            'error': note.priority === 3,
            'normal': !note.priority
        },{'done':note.isDone}]"
         class="note">
            <div class="note--info">
                <h3>
                    {{ note.id }}{{ note.title }}
                </h3>
                <p>
                    {{ note.content }}
                </p>
            </div>
            <div class="note-actions">
                <Button @click="$emit('finNote',note.id)" size="small" type="text" >{{note.isDone?"未完成":"已完成"}}</Button>
                <Button @click="$emit('delNote',note.id)" size="small" type="text">刪除</Button>

            </div>

        </li>
    </ul>
</template>
   


<style scoped>
ul,
li,
h3,
p {
    padding: 0;
    margin: 0;
}

.note-list {
    list-style: none;
    display: flex;
    flex-direction: column;
    /* width: 100%; */
    gap: 16px;

}

.note {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 16px;
    border-radius: 16px;
    min-height: 80px;
    transition: 200ms;

}

.note:hover {
    box-shadow: 0 0 10px #999;
}

.note--info {
    display: flex;
    flex-direction: column;
    gap: 4px;
}

.note-actions {
    display: flex;
    gap: 8px;
}

.note.primary {
    background: rgba(63, 146, 255, 0.2);
}

.note.warning {
    background: rgba(255, 165, 0, 0.2);
}

.note.error {
    background: rgba(255, 0, 0, 0.2);
}

.note.normal {
    background: #FFF;
}

.note.done{
    background: #EEE;
    color: #999;
}
</style>