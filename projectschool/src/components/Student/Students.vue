<template>
  <div>
    <Title text="Student" />
    <input
      type="text"
      placeholder="Studentes's name"
      v-model="name"
      v-on:keyup.enter="addStudent()"
    />
    <button class="btn btnInput" @click="addStudent()">Add</button>

    <table>
      <thead>
        <th>Number</th>
        <th>Name</th>
        <th>Options</th>
      </thead>
      <tbody v-if="students.length">
        <tr v-for="(student, index) in students" :key="index">
          <td>{{ student.id }}</td>
          <!-- <td>{{student.id}}</td> -->
          <td>{{ student.name }} {{ student.surname }}</td>
          <td>
            <button class="btn btn_danger" @click="removeStudent(student)">
              Remove
            </button>
          </td>
        </tr>
      </tbody>
      <tfoot v-if="!students.length">
        Student not found!
      </tfoot>
    </table>
  </div>
</template>

<script>
import Title from "../_shared/Title.vue";
export default {
  components: {
    Title,
  },
  data() {
    return {
      title: "Student",
      name: "",
      students: [],
    };
  },
  created() {
    this.$http
      .get("http://localhost:3000/students")
      .then((res) => res.json())
      .then((students) => (this.students = students));
  },
  props: {},
  methods: {
    addStudent() {
      let _student = {
        name: this.name,
        surname: "",
      };

      this.$http
        .post("http://localhost:3000/students", _student)
        .then((res) => res.json())
        .then((studentOutput) => {
          this.students.push(studentOutput);
          this.name = "";
        });
    },
    removeStudent(student) {
      this.$http
        .delete(`http://localhost:3000/students/${student.id}`)
        .then(() => {
          let index = this.students.indexOf(student);
          this.students.splice(index, 1);
        });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
input {
  width: calc(100% - 195px);
  border: 0;
  padding: 20px;
  font-size: 1.3em;
  color: #687f7f;
  display: inline;
}
.btnInput {
  width: 150px;
  border: 0px;
  padding: 20px;
  font-size: 1.3em;
  display: inline;
  background-color: rgb(116, 115, 115);
}
.btnInput:hover {
  padding: 20px;
  margin: 0px;
  border: 0px;
}
</style>
