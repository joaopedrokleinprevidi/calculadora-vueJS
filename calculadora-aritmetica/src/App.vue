

<script setup>

let valor01;
let valor02;
let sinal;
let valorExibido;



function resgatarValor01(event){
  valor01 = event.target.value;
  console.log(valor01)
}

function resgatarValor02(event){
    valor02 = event.target.value;
    console.log(valor02)
}

function recebeSinal(event){
    sinal = String(event.target.value);
    console.log(sinal)
}

function realizaCalculo(){
  if (!sinal == '' && !valor01 == undefined && !valor02 == undefined){
    switch(sinal) {
      case '+':
        valorExibido = valor01 + valor02;
        break;
      case '-':
        valorExibido = valor01 - valor02;
        break
      case '*':
        valorExibido = valor01 * valor02;
        break
      case '/':
        valorExibido = valor01 / valor02;
        break;
      default:
        alert('Erro encontrado, pedimos desculpas e instruimos a atualizar a página e tentar novamente.')
    }

    valor01 = '';
    valor02 = '';
    sinal = '';
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
      <input type="number" @change="resgatarValor01(); realizaCalculo()" class="gap number" id="number01">
      <select @change="recebeSinal(); realizaCalculo()" id="selecione" class="gap number">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">*</option>
        <option value="/">/</option>
      </select> 
      <input type="number" @change="resgatarValor02(); realizaCalculo()" class="gap number" id="number02">
    </section>
    <p class="flex resultado">Resultado: {{ valorExibido }}</p>
    
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
