<template>
  <div>
      <Title text="Professor" />
    <table>
      <thead>
        <th>Number</th>
        <th>Name</th>
        <th>Amount Students</th>
      </thead>
      <tbody v-if="professors.length">
        <tr v-for="(professor, index) in professors" :key="index">
          <td>{{professor.id}}</td>
          <td>{{ professor.name }} {{ professor.surname }}</td>
          <td>
              3
          </td>
        </tr>
      </tbody>
      <tfoot v-else>
        Professor not found!
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
        professors: [
            {id: 1, name: 'Ana'},
            {id: 2, name: 'Lucas'},
            {id: 3, name: 'Rodrigo'}
        ]
    };
  },
};
</script>

<style scoped></style>
