<template>
    <div @dblclick="$emit('toggle-reminder',  task.id)" :class="[task.reminder ? 'reminder' : '', 'task']">
        <h3>{{ task.text }}
            <i @click="$emit('delete-task', task.id)" class="fa-solid fa-circle-xmark"></i>
        </h3>
        <p>{{ task.day }}</p>
    </div>
</template>

<script>
export default {
    name: "Task",
    props: {
        task: Object
    },
   
}
</script>

<style scoped>
.task {
    background-color: rgb(202, 202, 202);
    border-radius: 5px;
    padding: 25px 15px;
    margin: 10px 0;
    line-height: 2;
    cursor: pointer;
}

.task.reminder {
    border-left: 5px solid green;
}

h3 {
    display: flex;
    justify-content: space-between;
    ;
}

.fa-solid {
    color: red;
    cursor: pointer;
}</style>