<template>
    <form @submit="onSubmit" class="form" action="">
        <div class="form-container">
            <div class="form-control">
                <label for="text">Task</label>
                <input v-model="text" type="text" id="text" name="text" placeholder="Add task">
            </div>
            <div class="form-control">
                <label for="day">Date & Time</label>
                <input v-model="day" type="text" id="day" name="day" placeholder="Add date & Time">
            </div>

            <div class="form-control">
                <label for="reminder">Set reminder</label>
                <input v-model="reminder" type="checkbox" id="reminder" name="reminder" placeholder="Add task">
            </div>
            <button class="btn">Save Task</button>
        </div>
    </form>
</template>

<script>
export default {
    name: "AddTask",
    data() {
        return {
            id: Math.floor(Math.random() * 1000000),
            text: '',
            day: '',
            reminder: false
        }
    },
    methods: {
        onSubmit(e) {
            e.preventDefault()
            if (!this.text) { 
                alert("Please add Task")
                return
            }
                
            const newTask = {
                id: Math.floor(Math.random() * 1000000),
                text: this.text,
                day: this.day,
                reminder: this.reminder
            }
            this.$emit("add-task", newTask)
            
        }
    }
}
</script>

<style scoped>
.form {
    margin: 40px 0;
}

.form-container {
    display: flex;
    flex-direction: column;
    gap: 20px;
}

.form-control {
    display: flex;
    flex-direction: column;
    gap: 5px;
    justify-content: center;

}

.btn {
    background-color: black;
}

label {
    font-weight: 500;
    font-size: 18px;
}

input {
    padding: 10px 5px;
    outline: none;
    font-size: 16px;

}

input[type='checkbox'] {
    width: 50px;
}

.form-control:last-of-type {
    flex-direction: row;
    justify-content: flex-start;
}</style>