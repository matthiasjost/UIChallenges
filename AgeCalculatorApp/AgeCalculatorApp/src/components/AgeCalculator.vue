<script setup lang="ts">
import { ref } from 'vue'

const InputDays = ref("");
const InputMonths = ref("");
const InputYears = ref("");

const CalculatedDays = ref("");
const CalculatedMonths = ref("");
const CalculatedYears = ref("");

function onSubmitForm()
{
  CalculatedDays.value = InputDays.value;
  CalculatedMonths.value = InputMonths.value;
  CalculatedYears.value = InputYears.value;
  InputDays.value = "";
  InputMonths.value = "";
  InputYears.value = "";
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
        <div @click="onSubmitForm" class="circle"></div>
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
