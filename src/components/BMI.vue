<template>
  <form v-on:submit="submitBMI">
    <h1>BMI CALCULATOR</h1>
    <div>
      <label for="weight">Weight: {{ weight }}</label>
      <input
        type="range"
        min="0"
        max="200"
        id="weight"
        step="1"
        v-model="weight"
      />
    </div>
    <div>
      <label for="height">Height: {{ height }}</label>
      <input
        type="range"
        min="0"
        max="250"
        id="height"
        step="1"
        v-model="height"
      />
    </div>
    <button type="submit">계산</button>
    <div v-if="calculatedBMI !== null" class="bmi-info">
      BMI 지수: {{ calculatedBMI }}
    </div>
    <br />
    <BMITable v-if="calculatedBMI !== null" />
  </form>
</template>

<script>
import BMITable from "./BMITable.vue";

export default {
  name: "BMI",
  components: {
    BMITable,
  },
  data() {
    return {
      weight: "",
      height: "",
      calculatedBMI: null,
    };
  },
  methods: {
    submitBMI(event) {
      event.preventDefault();
      const calculatedHeight = this.height / 100;
      const result = this.weight / (calculatedHeight * calculatedHeight);
      if (isNaN(result)) {
        alert("키와 몸무게를 입력해주세요.");
        this.calculatedBMI = null;
      } else {
        this.calculatedBMI = result.toFixed(1);
      }
    },
  },
};
</script>

<style scoped>
.bmi-info {
  margin-top: 10px;
}
</style>
