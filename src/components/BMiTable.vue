<template>
  <div class="bmi-table">
    <table>
      <thead>
        <tr>
          <th v-for="column in columns" :key="column">{{ column }}</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in data" :key="index">
          <td>{{ item.체질량지수 }}</td>
          <td>{{ item.분류 }}</td>
          <td>{{ item.체중범위 }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import data from "../mocks/BMIData.ts";

export default {
  name: "BMITable",
  data() {
    return {
      columns: ["체질량지수", "분류", "체중범위"],
      data,
    };
  },
};
</script>

<style scoped>
.bmi-table {
  display: flex;
  justify-content: center;
}
</style>
