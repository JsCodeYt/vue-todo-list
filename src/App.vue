<template>
  <div class="App">
    <div class="tasks__container">
      <HeaderVue @handleData="handleData" />
      <TasksVue :tasks="tasks" @handleDeleteData="handleDelete" />
    </div>
  </div>
</template>
<script>
import HeaderVue from './components/Header.vue';
import TasksVue from './components/Tasks.vue';
export default {
  data() {
    return {
      tasks: JSON.parse(localStorage.getItem("data")) || [],
    }
  },
  components: {
    HeaderVue,
    TasksVue,
  },
  methods: {
    handleData(item) {
      const newTask = {
        id: Date.now(),
        name: item,
      }
      this.tasks.unshift(newTask)
      localStorage.setItem("data", JSON.stringify([...this.tasks]))
    },
    handleDelete(id) {
      this.tasks.map((item, index) => {
        if (item.id === id) {
          this.tasks.splice(index === 0 ? null : index, index + 1)
          localStorage.setItem("data", JSON.stringify([...this.tasks]))
        }
      })
    },
  }
}
</script>
<style lang="scss">
.App {
  display: flex;
  align-items: center;
  justify-content: center;

  .tasks__container {
    height: 600px;
    margin: 50px 0px;
    width: 500px;
    background-color: #fff;
    border: 1px solid #000;
    border-radius: 10px;
    overflow: auto;
  }
}
</style>