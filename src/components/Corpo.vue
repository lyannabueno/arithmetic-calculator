<script setup>
import { reactive } from 'vue';

const estate = reactive({
    number1: '',
    number2: '',
    arithmeticOperations: 'add',

    operations: {
        add: (a, b) => a + b,
        subtract: (a, b) => a - b,
        multiply: (a, b) => a * b,
        divide: (a, b) => a / b
    },

    result: ''
})

const calculate = () => {
    const { number1, number2, arithmeticOperations } = estate

    if (number1 !== '' && number2 !== '') {
        estate.result = estate.operations[arithmeticOperations](parseFloat(number1), parseFloat(number2))
    } else {
        estate.result = ''
    }
}
</script>

<template>
    <div class="container pt-5 pb-5">
        <h1 class="text-center">Calculadora Aritmética</h1>

        <div class="d-grid">
            <div class="calculator">
                <input v-model="estate.number1" type="number" placeholder="1º número" class="form-control border-color" required @input="calculate">
                <input v-model="estate.number2" type="number" placeholder="2º número" class="form-control border-color mt-5 mb-5" required @input="calculate">
                <h6> Resultado... {{ estate.result }} </h6>
            </div>

            <select v-model="estate.arithmeticOperations" class="form-control choices" @change="calculate">
                <option value='add'>+</option>

                <option value='subtract'>-</option>

                <option value='multiply'>x</option>

                <option value='divide'>÷</option>
            </select>
        </div>
    </div>
</template>

<style scoped>
h1 {
    padding-bottom: 50px;
    font-family: "Roboto Slab", serif;
    font-weight: 300;

}

h6 {
    font-family: "Roboto Slab", serif;
    font-weight: 300;
    color: gray;
}

input .form-control {
    width: 15vh;
}

.d-grid {
    grid-template-columns: repeat(2, 200px);
    justify-content: center;
}

.choices {
    display: block;
    width: 5vh;
    text-align: center;
    margin-left: auto;
    height: 5vh;
}

option {
    font-size: 20px;
}

i {
    color: rgb(42, 188, 236);
}

.border-color {
    border-color: rgb(212, 212, 212);
}
</style>