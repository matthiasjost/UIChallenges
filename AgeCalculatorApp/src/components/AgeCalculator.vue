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

function calculateAge(inputYearsInt: number, inputMonthsInt: number, inputDaysInt: number) {
    const today = new Date();
    const birthday = new Date(inputYearsInt, inputMonthsInt - 1, inputDaysInt);
    let yearDiff = today.getFullYear() - birthday.getFullYear();
    let monthDiff = today.getMonth() - birthday.getMonth();
    let dayDiff = today.getDate() - birthday.getDate();

    if (dayDiff < 0) {
        monthDiff--;
        const monthDays = new Date(today.getFullYear(), today.getMonth(), 0).getDate();
        dayDiff += monthDays;
    }

    if (monthDiff < 0) {
        yearDiff--;
        monthDiff += 12;
    }

    const outputYearsInt = yearDiff;
    const outputMonthsInt = monthDiff;
    const outputDaysInt = dayDiff;

    return { outputYearsInt, outputMonthsInt, outputDaysInt };
}

function onSubmitForm() {

    DaysValidationError.value = "Error";
    MonthsValidationError.value = "Error";
    YearsValidationError.value = "Error";

    const inputYearsInt = parseInt(InputYears.value);
    const inputMonthsInt = parseInt(InputMonths.value);
    const inputDaysInt = parseInt(InputDays.value);

    const resultValues = calculateAge(inputYearsInt, inputMonthsInt, inputDaysInt);

    CalculatedDays.value = String(resultValues.outputDaysInt);
    CalculatedMonths.value = String(resultValues.outputMonthsInt);
    CalculatedYears.value = String(resultValues.outputYearsInt);

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
                    <span class="timespan-item"><span class="number">{{ CalculatedYears }}</span> years</span>
                </div>
                <div class="grid-row-1-col-3">
                    <span class="timespan-item"><span class="number">{{ CalculatedMonths }}</span> month</span>
                </div>
                <div class="grid-row-1-col-3">
                    <span class="timespan-item"><span class="number">{{ CalculatedDays }}</span> days</span>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
</style>
