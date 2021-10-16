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
          <td>{{ task.status }}</td>
          <td class="text-center"><i class="fa fa-pen"></i></td>
          <td class="text-center"><i class="fa fa-trash"></i></td>
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
      if (this.task.length > 0)
        this.tasks.push({
          name: this.task,
          status: "to-do",
        });

      return;
    },
  },
};
</script>

<style scoped></style>
