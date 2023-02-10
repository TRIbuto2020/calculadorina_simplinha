<script setup>
  import { reactive } from 'vue';

  const estado = reactive({
    itemUm: 0,
    itemDois: 0,
    operacao: 'soma',
  });

  const resolve = () => {
    const {operacao} = estado;

    switch(operacao){
      case 'sub':
        return parseFloat(estado.itemUm) - parseFloat(estado.itemDois);
      case 'mult':
        return parseFloat(estado.itemUm) * parseFloat(estado.itemDois);
      case 'div':
        return parseFloat(estado.itemUm) / parseFloat(estado.itemDois);
      default:
        return parseFloat(estado.itemUm) + parseFloat(estado.itemDois);
    };
  };
</script>

<template>
  <div>
    <h1>Calculadorinha Simplinha</h1>
    <form>
      <input type="number" :value="estado.itemUm" @change="evento => estado.itemUm = evento.target.value" @keyup="evento => estado.itemUm = evento.target.value" min="0">
      <select @change="evento => estado.operacao = evento.target.value">
        <option value="soma">+</option>
        <option value="sub">-</option>
        <option value="mult">x</option>
        <option value="div">/</option>
      </select>
      <input type="number" :value="estado.itemDois" @change="evento => estado.itemDois = evento.target.value" @keyup="evento => estado.itemDois = evento.target.value" min="0">
    </form>
    <h2>= {{ resolve() }}</h2>
  </div>
</template>

<style scoped>
  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: sans-serif;
    color: #ddd;
  }

  div{
    width: 900px;
    height: 100vh;
    max-width:80%;
    margin: auto;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  h1{
    margin-bottom: 48px;
    font-size: 40px;
    text-align: center;
  }

  form{
    margin: 0 auto;
    display: flex;
    gap: 10%;
  }
  
  select{
    width: 20%;
  }
  
  input, select{
    text-align: center;
    font-size: 28px;
    width: 40%;
    background-color: #333;
    padding: 8px;
    border: #ddd solid 1px;
  }

  h2{
    margin-top: 40px;
    font-size: 36px;
  }

</style>
