<script setup>
import { reactive } from 'vue';

const estate = reactive({
    number1: '',
    number2: '',

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

    estate.result = estate.operations[arithmeticOperations](parseFloat(number1), parseFloat(number2))
}
</script>

<template>
    <div class="container pt-5 pb-5">
        <h1 class="text-center">Calculadora Aritmética</h1>

        <div class="d-grid">
            <div class="calculator">
                <input v-model="estate.number1" type="number" placeholder="1º número" class="form-control border-color" required @input="calculate">
                <input v-model="estate.number2" type="number" placeholder="2º número" class="form-control border-color mt-5 mb-5" required @input="calculate">
                <h3> Resultado...{{ estate.result }} </h3>
            </div>

            <select v-model="estate.arithmeticOperations" class="choices" @change="calculate">
                <button type="button" class="btn btn-outline-dark border-color mt-1" value='add'">
                    <i class=" fa fa-plus"></i>
                </button>

                <button type="button" class="btn btn-outline-dark border-color mt-3 mb-3" value='subtract'">
                    <i class=" fa fa-minus"></i>
                </button>

                <button type="button" class="btn btn-outline-dark border-color mb-3" value='multiply'">
                    <i class=" fa fa-x"></i>
                </button>

                <button type="button" class="btn btn-outline-dark border-color" value='divide'">
                    <i class=" fa fa-divide"></i>
                </button>
            </select>
        </div>
    </div>
</template>

<style scoped>
h1 {
    padding-bottom: 50px;
}

.form-control {
    width: 15vh;
}

.d-grid {
    grid-template-columns: repeat(2, 200px);
    justify-content: center;
}

.choices button {
    display: block;
    margin-left: auto;
    width: 5vh;
}

i {
    color: rgb(42, 188, 236);
}

.border-color {
    border-color: rgb(212, 212, 212);
}
</style>