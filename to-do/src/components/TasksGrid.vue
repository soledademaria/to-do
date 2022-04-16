<template>
  <div class="tasks-grid">
    <task-item v-for="task in tasks" :key="task.name" :task="tasks"/>
      
   
  </div>
</template>
<script>
import TaskItem from './TaskItem.vue'
export default {
    components: {TaskItem},
    // props: {
    //     tasks: {type: Array, required: true}
    // },
    data(){
        return{
            tasks: [
                {name: 'Lavar a louça', pending: true},
                {name: 'Limpar a casa', pending: false},
                {name: 'Preparar o almoço', pending: true},
                {name: 'Terminar leitura', pending: true}
            ]
        }
    }
}
</script>
<style>
    .task-grid{
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
    }
    .task-grid .task{
        margin: 10px;
    }
    .no-task{
        color: #aaa;
        font-size: 1.7em;
    }
</style>