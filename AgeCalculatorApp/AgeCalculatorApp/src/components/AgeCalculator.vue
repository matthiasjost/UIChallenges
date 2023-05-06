<script setup lang="ts">
import { ref } from 'vue'
import { computed } from 'vue'

const InputDays = ref(1);
const InputYears = ref(1);
const InputMonths = ref(1);


const CalculatedYears = computed(() => {
  return InputYears;
});

const CalculatedMonths = computed(() => {
  return InputMonths;
});

const CalculatedDays = computed(() => {
  return InputDays;
});

</script>

<template>
  <div id="main-container">
    <div id="main-card">
      <div class="grid">
        <div class="grid-row-1-col-1 grid-row-base">
          <div class="form-combo">
            <label for="day">Day</label>
            <input v-model="InputDays" type="number" id="days"/>
          </div>
        </div>
        <div class="grid-row-1-col-1 grid-row-base">
          <div class="form-combo">
            <label for="month">Month</label>
            <input v-model="InputMonths" type="number" id="months"/>
          </div>
        </div>
        <div class="grid-row-1-col-1 grid-row-base">
          <div class="form-combo">
            <label for="years">Year</label>
            <input v-model="InputYears" type="number" id="years"/>
          </div>
        </div>
        <div class="grid-row-1-col-3 grid-row-base">
          <span class="timespan-item">{{ CalculatedDays }} days</span>
        </div>
        <div class="grid-row-1-col-3 grid-row-base">
          <span class="timespan-item">{{ CalculatedMonths }} month</span>
        </div>
        <div class="grid-row-1-col-3 grid-row-base">
          <span class="timespan-item">{{ CalculatedYears }} years</span>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
</style>
