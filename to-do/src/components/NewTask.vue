<template>
    <div class="new-task">
        <input v-model="name"
        type="text"
        class="form"
        @keydown.enter="addTask"
        placeholder="Nova tarefa">

        <button class="form" @click="addTask">+</button>
    </div>
</template>
<script>
export default {
    data(){
        return{
            name: ''
        }
    },
    methods:{
        addTask(){
            this.$emit('taskAdded', {name: this.name})
            this.name = ''
        }
    }
}
</script>
<style scoped>
    .new-task{
        margin: 35px;
    }
    .form{
        outline: none;
        font-size: 2rem;
        border: 2px solid #fff;
        padding: 5px 10px 8px;
        color:#fff
    }
    input.form
    {
        width: 500px;
        background: #fff2;
        border-top-left-radius: 8px;
        border-bottom-left-radius: 8px;
    }
    button.form{
        border-left: none;
        background-color: #2196f3;
        border-top-right-radius: 8px;
        border-bottom-right-radius: 8px;

    }
</style>