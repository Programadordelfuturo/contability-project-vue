<template>
  <div class="bg-cyan-600 w-[55%] m-auto rounded-md">
    <h1 class="bg-slate-400 text-5xl py-2 rounded-md">
      Asistente Contable
      <font-awesome-icon :icon="['fas', 'user-secret']" class="mx-3"/>  
    </h1>
    <div class="gap-3 my-2 py-3">
      <p>
        <strong>Base Imponible: </strong>
      </p>
      <input class="rounded-md" type="text" v-model="base">
      <p class="">
        <strong>IVA (19%):</strong>
      </p>
      <div>
        {{ initCalculate(base) }} $
      </div>
      <p>
        <strong>Total a cobrar a cliente final:</strong>
      </p>
      <div>
        {{ sumTotalVenta(base) || 0 }} $
      </div>
    </div>
    <div class="gap-3 my-2 py-3">
      <p>
        <strong>Sumatoria de base imponible de tus compras</strong>
      </p>
      <input class="rounded-md" type="text" v-model="bcc">
      <p>
        <strong>IVA (19%):</strong>
      </p>
      <div>
        {{ initCalculate(bcc) }} $
      </div>    
      <p>
        <strong>Sumatoria total de compras</strong>
      </p>
      <div>
        {{ sumTotalVenta(bcc) || 0 }} $
      </div>
    </div>
    <div class="gap-3 my-2 py-3">
      <p>
        <strong>Sumatoria de base imponible de tus ventas</strong>
      </p>
      <input class="rounded-md" type="text" v-model="bvc">
      <p>
        <strong>IVA (19%):</strong>
      </p>
      <div>
        {{ initCalculate(bvc) }} $
      </div>
      <p>
        <strong>Sumatoria total de ventas</strong>
      </p>
      <div>
        {{ sumTotalVenta(bvc) || 0 }} $
      </div>
    </div>
    <div>
      <strong>Diferencia a <br/>abonar a la entidad: </strong>
      <p>{{ ivaDifference(bvc, bcc) || 0 }} $ </p>
    </div>
  </div>
</template>

<script>
import './assets/tailwind.css'
import { defineComponent } from "vue";
// import {} from 'fontasome'

export default defineComponent({
  data() {
    return {
      base: '',
      bcc: '',
      bvc: ''
    }
  },
  methods: {
    initCalculate(e) {
      const value = Number(e)
      return value*0.19
    },
    sumTotalVenta(e) {
      const value = Number(e)
      return value + value*0.19
    },
    ivaDifference(e, i){
      const ivaVenta = Number(e)
      const ivaCompra = Number(i)
      return ivaVenta*0.19 - ivaCompra*0.19
    }
  }
})
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}



</style>