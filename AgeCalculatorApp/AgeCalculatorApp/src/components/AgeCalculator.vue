<script setup lang="ts">
import { ref } from 'vue'

const InputDays = ref(5);
const InputMonths = ref(7);
const InputYears = ref(1985);

const CalculatedDays = ref(1);
const CalculatedYears = ref(1);
const CalculatedMonths = ref(1);

function onCalculateAge()
{
  /*var birthDate = new Date(year, month - 1, day);
  var age = today.getFullYear() - birthDate.getFullYear();
  var m = today.getMonth() - birthDate.getMonth();*/


  CalculatedDays.value = InputDays.value;
  CalculatedDays.value = InputDays.value;
  CalculatedDays.value = InputDays.value;
  CalculatedDays.value = InputDays.value;
}

</script>

<template>
  <div id="main-container">
    <div id="main-card">
      <div class="grid">
        <div class="grid-row-1-col-1">
          <div class="form-combo">
            <label for="days">Day</label>
            <input v-model="InputDays" type="number" id="days"/>
          </div>
        </div>
        <div class="grid-row-1-col-1">
          <div class="form-combo">
            <label for="months">Month</label>
            <input v-model="InputMonths" type="number" id="months"/>
          </div>
        </div>
        <div class="grid-row-1-col-1">
          <div class="form-combo">
            <label for="years">Year</label>
            <input v-model="InputYears" type="number" id="years"/>
          </div>
        </div>
        <div class="grid-row-1-col-3">
          <div class="line"></div>
        </div>
        <div @click="onCalculateAge" class="circle"></div>
        <div class="grid-row-1-col-3">
            <span class="timespan-item"><span class="number">{{ CalculatedDays }}</span> days</span>
        </div>
        <div class="grid-row-1-col-3">
          <span class="timespan-item"><span class="number">{{ CalculatedMonths }}</span> month</span>
        </div>
        <div class="grid-row-1-col-3">
          <span class="timespan-item"><span class="number">{{ CalculatedYears }}</span> years</span>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
</style>
