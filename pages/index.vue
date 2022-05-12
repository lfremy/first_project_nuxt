
<template>
  <main class="bg-red-500 text-center">
    <h1>TODO</h1>
    <p>Crée une liste de tâches</p>

    <div >
      <input 
      class="bg-yellow-200"
        type="text" 
        v-model="newTask" 
        placeholder="Add a new task" 
        @keypress.enter="addTask" />
      <button @click="addTask">Add</button>
    </div>

    <div class="tasks bg-gray-500 ">
      <Task class='flex justify-around'
        v-for="(task, i) in $store.state.tasks"
        :key="i"
        :task="task" />
    </div>

  </main>
</template>

<script>
export default {
  data (){
    return {
      newTask: ''
    }
  },
  methods: {
    addTask () {
      if (this.newTask) {
        this.$store.commit('ADD_TASK', this.newTask);
        this.newTask = '';
      }
    }
  }
}
</script>
