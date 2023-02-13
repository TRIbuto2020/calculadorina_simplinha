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
    <h1>Calcule!</h1>
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
</style>
