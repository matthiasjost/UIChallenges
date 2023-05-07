<script lang="ts" setup>
import {ref} from 'vue'

const InputDays = ref("");
const InputMonths = ref("");
const InputYears = ref("");

const CalculatedDays = ref("");
const CalculatedMonths = ref("");
const CalculatedYears = ref("");

const DaysValidationError = ref("Error");
const MonthsValidationError = ref("");
const YearsValidationError = ref("");

function onSubmitForm() {

    DaysValidationError.value = "Error";
    MonthsValidationError.value = "Error";
    YearsValidationError.value = "Error";

    const today = new Date();

    debugger;

    const inputYearsInt = parseInt(InputYears.value);
    const inputMonthsInt = parseInt(InputMonths.value);
    const inputDaysInt = parseInt(InputDays.value);

    const outputYearsInt = today.getFullYear() - inputYearsInt;
    const outputMonthsIn = today.getMonth() - inputMonthsInt;
    const outputDaysInt = today.getDay() - inputDaysInt;

    CalculatedDays.value = String(outputDaysInt);
    CalculatedMonths.value = String(outputMonthsIn);
    CalculatedYears.value = String(outputYearsInt);


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
                        <label class="input-labels" for="days">Day</label>
                        <input id="days" v-model="InputDays" type="number"/>
                        <span id="daysValidationError" class="validation-error">{{ DaysValidationError }}</span>
                    </div>
                </div>
                <div class="grid-row-1-col-1">
                    <div class="form-combo">
                        <label class="input-labels" for="months">Month</label>
                        <input id="months" v-model="InputMonths" type="number"/>
                        <span id="monthsValidationError" class="validation-error">{{ MonthsValidationError }}</span>
                    </div>
                </div>
                <div class="grid-row-1-col-1">
                    <div class="form-combo">
                        <label class="input-labels" for="years">Year</label>
                        <input id="years" v-model="InputYears" type="number"/>
                        <span id="yearsValidationError" class="validation-error">{{ YearsValidationError }}</span>
                    </div>
                </div>
                <div class="grid-row-1-col-3">
                    <div class="line"></div>
                </div>
                <div class="circle" @click="onSubmitForm"></div>
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
