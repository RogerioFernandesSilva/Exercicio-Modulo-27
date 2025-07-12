<script setup>
  import { reactive, watch } from 'vue';
  import Title from './components/Title.vue';
  import SetNumberOne from './components/SetNumberOne.vue';
  import SetNumberTwo from './components/SetNumberTwo.vue';
  import Operation from './components/Operation.vue';
  import Result from './components/Result.vue';

  const estado = reactive({
    operacao: '-',
    num1: 0,
    num2: 0,
    resultado: 0
  });

  const getNumeroOne = ev => estado.num1 = Number(ev.target.value);
  const getNumeroTwo = ev => estado.num2 = Number(ev.target.value);
  const mudaOperacao = ev => estado.operacao = ev.target.value;
  

  watch( () => [estado.operacao, estado.num1, estado.num2], () => {
    switch (estado.operacao) {
    case '+':
      estado.resultado = estado.num1 + estado.num2;
      break;
    case '-':
      estado.resultado = estado.num1 - estado.num2;
      break;
    case 'x':
      estado.resultado = estado.num1 * estado.num2;
      break;
    case '/':
      estado.resultado = estado.num2 !== 0 ? estado.num1 / estado.num2 : 'Erro: Divisão por zero';
      break;
    default: 
      estado.resultado = 0;
    }
  }, {immediate: true});

</script>

<template>
  <div class="container">
    <Title/>
    <SetNumberOne :pega-numero1="getNumeroOne" />
    <Operation :show-operation="mudaOperacao" :operation="estado.operacao"/>
    <SetNumberTwo :pega-numero2="getNumeroTwo" />
    <Result :results="estado.resultado" />
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'poppins', sans-serif;
}
.container {
  background:  #f5f5f5;
  max-width: 450px;
  margin: 70px auto;
  padding: 15px 20px;
  border: 2px solid black;
  border-radius: 20px;
  color: #080707;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.grupo-input,
.set-operacao {
  display: flex;
  flex-direction: column;
  gap: 5px;
}
.view-operacao {
  text-align: center;
  font-style: bold;
  font-size: 1rem;
}

input,
select {
  display: block;
  width: 100%;
  padding: 8px 20px;
  border: 2px solid #0e0d0d;
  outline: none;
  cursor: pointer;
  font-size: 1rem;
} 

h1,
h2,
span {
  text-align: center;
}

h1 {
  margin-bottom: 10px;
}
span {
  font-size: 2rem;
  font-weight: bold;
  margin-top: 10px;
}
.erro {
  color: #f50404;
}
</style>