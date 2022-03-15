<template>
<div>
    <input type="text" v-model="addingTask"/>
    <button @click="addTask(addingTask.name)"></button>
    <ul>
        <li v-for="task in taskCheSonoVisibili" :key="task.id">
            {{task.name}}
        </li>
    </ul>
</div>
</template>

<script>
export default {
  name: 'ToBeFixed',
  data: function() {
    return {
      tasks: [],
      addingTask: undefined
    }
  },
  methods: {
    addTask(taskName) {
        this.tasks.push({
            name: taskName
        })
    },
    removeTask(taskName) {
        const index = this.tasks.indexOf({name: taskName})
        this.tasks = this.tasks.slice(index, 0)
    }
  },
  computed: {
      allTasks: function() {
        return this.tasks.filter(t => !!t.name && !!t.visible)   
      },
      taskCheSonoVisibili: function() {
        return this.tasks.filter(t => !!t.name)
      },
      taskInvisibili: function() {
        return this.tasks.filter(t => !t.visibile)
      },
  }
};
</script>
