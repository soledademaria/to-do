<template>
  <div class="tasks-grid">
      <template v-if="tasks.length">
          <task-item v-for="task in tasks" :key="task.name" :task="task"/>
      </template>
      <p v-else class="no-task">
          Ops, você não possui tarefas cadastradas!!
      </p>
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
    .tasks-grid{
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
    }
    .tasks-grid .task{
        margin: 10px;
    }
    .no-task{
        color: #aaa;
        font-size: 1.7em;
    }
</style>