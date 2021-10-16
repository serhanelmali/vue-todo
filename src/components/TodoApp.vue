<template>
  <div class="container">
    <h2 class="text-center mt-5">Vue Todo App</h2>

    <div class="d-flex">
      <input type="text" placeholder="Enter Task" class="form-control" />
      <button class="btn btn-warning rounded-0">SUBMIT</button>
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
        <tr>
          <td>Learn Vue</td>
          <td>To-do</td>
          <td></td>
          <td></td>
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
};
</script>

<style scoped></style>
