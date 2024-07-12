<script setup>
import { ref, computed } from 'vue';

const num1 = ref(0);
const num2 = ref(0);
const operacao = ref('adicao');

const resultado = computed(() => {
    switch (operacao.value) {
        case 'adicao':
            return num1.value + num2.value;
        case 'subtracao':
            return num1.value - num2.value;
        case 'multiplicacao':
            return num1.value * num2.value;
        case 'divisao':
            return num2.value !== 0 ? num1.value / num2.value : 'Erro: Divisão por zero';
        default:
            return 0;
    }
});
</script>

<template>
  <div id="app" class="container">
    <h1>Calculadora Aritmética</h1>
    <div class="form-group">
      <label for="num1">Número 1:</label>
      <input v-model.number="num1" id="num1" type="number" class="form-control">
    </div>
    <div class="form-group">
      <label for="num2">Número 2:</label>
      <input v-model.number="num2" id="num2" type="number" class="form-control">
    </div>
    <div class="form-group">
      <label for="operacao">Operação:</label>
      <select v-model="operacao" id="operacao" class="form-control">
        <option value="adicao">+</option>
        <option value="subtracao">-</option>
        <option value="multiplicacao">*</option>
        <option value="divisao">/</option>
      </select>
    </div>
    <div class="result">
      Resultado: {{ resultado }}
    </div>
  </div>
</template>

<style scoped>
.container {
  max-width: 500px;
  margin: 0 auto;
  padding: 2rem;
  background-color: #f5f5f5;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}
.form-group {
  margin-bottom: 1rem;
}
.form-control {
  width: 100%;
  padding: 0.5rem;
  margin-top: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 5px;
}
.result {
  margin-top: 1rem;
  font-size: 1.5rem;
  font-weight: bold;
}
</style>
