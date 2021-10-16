<template>
  <div class="container">
    <h2 class="text-center mt-5">Vue Todo App</h2>

    <div class="d-flex">
      <input
        v-model="task"
        type="text"
        placeholder="Enter Task"
        class="form-control"
      />
      <button @click="submitTask" class="btn btn-warning rounded-0">
        SUBMIT
      </button>
    </div>

    <table class="table table-bordered mt-5">
      <thead>
        <tr>
          <th scope="col">Task</th>
          <th scope="col">Status</th>
          <th scope="col" class="text-center">#</th>
          <th scope="col" class="text-center">#</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(task, index) in tasks" :key="index">
          <td>{{ task.name }}</td>
          <td style="width: 120px">
            <span @click="changeStatus(index)" class="pointer">{{
              firstCharUpper(task.status)
            }}</span>
          </td>
          <td @click="editTask(index)" class="text-center">
            <i class="fa fa-pen"></i>
          </td>
          <td @click="deleteTask(index)" class="text-center">
            <i class="fa fa-trash"></i>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },

  data() {
    return {
      task: "",
      editedTask: null,
      statuses: ["todo", "in-progress", "finished"],
      tasks: [
        {
          name: "Search about Vue.",
          status: "to-do",
        },
        {
          name: "Learn Vue ASAP",
          status: "in-progress",
        },
      ],
    };
  },

  methods: {
    submitTask() {
      if (this.task.length === 0) return;

      if (this.editedTask === null)
        this.tasks.push({
          name: this.task,
          status: "to-do",
        });
      else {
        this.tasks[this.editedTask].name = this.task;
        this.editedTask = null;
      }

      this.task = "";
    },

    deleteTask(index) {
      this.tasks.splice(index, 1);
    },

    editTask(index) {
      this.task = this.tasks[index].name;
      this.editedTask = index;
    },

    changeStatus(index) {
      let newIndex = this.statuses.indexOf(this.tasks[index].status);

      if (++newIndex > 2) newIndex = 0;
      this.tasks[index].status = this.statuses[newIndex];
    },

    firstCharUpper(str) {
      return str.charAt(0).toUpperCase() + str.slice(1);
    },
  },
};
</script>

<style scoped>
.pointer {
  cursor: pointer;
}
</style>
