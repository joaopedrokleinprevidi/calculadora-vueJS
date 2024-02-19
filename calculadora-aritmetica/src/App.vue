<script setup>
import { reactive } from 'vue'

const estadoReativo = reactive({
  valorExibido: 0
})

let valor01;
let valor02;
let sinal;
let array;

function realizaCalculo(){
  if ((sinal !== undefined && sinal !== '') && (valor01 !== undefined && valor01 !== '') && (valor02 !== undefined && valor02 !== '')){
    array = String(valor01) + " " + String(sinal) + " " + String(valor02);
    estadoReativo.valorExibido = eval(array)
  }
}
</script>

<template>

  <header class="flex column">
    <h1>Calculadora Aritmética</h1>
    <h2>Digite os valores e selecione o sinal</h2>
  </header>
  
  <main>

    <section class="calculadora flex">
      <input type="number" @change="realizaCalculo()" v-model="valor01" class="gap number" id="number01">
      <select @change="realizaCalculo()" v-model="sinal" id="selecione" class="gap number">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">*</option>
        <option value="/">/</option>
      </select> 
      <input type="number" @change="realizaCalculo()" v-model="valor02" class="gap number" id="number02">
    </section>
    <p class="flex resultado">Resultado: {{ estadoReativo.valorExibido }}</p>
    
  </main>
  
</template>

<style scoped>

* {
  padding: 0px;
  margin: 0px;
  
}

.flex {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: lightblue;
}
.column {
  flex-direction: column;
}

header > h1 {
  text-shadow: 1px 1px 1px white;
  margin: 2rem;
}

.calculadora {
  padding-bottom: 1rem;
}

.number {
  padding: .3rem;
  width: 75px;
  font-size: 1.7rem;
}

.gap {
  margin: .5rem .5rem 0rem .5rem
}

.resultado {
    padding: 1rem;
    font-size: 2rem;
}
</style>
