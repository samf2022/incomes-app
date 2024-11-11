<template>
  <div>
    <h1>Incomes app</h1>
    <div class="input-containers">
      <!-- <div style="width:120px;" v-for="(item, itemName) in items" :key="itemName" class="block">
        <span>{{ item.icon }}</span>
        <input
          style="width: 30px;"
          type="text"
          v-model.number="item.quantity"
          placeholder="amount"
        >
        <span>:{{ item.quantity * item.price }}</span>
      </div> -->

      <div v-for="(item, itemName) in items" :key="itemName" style="border-radius: 5px; width: 100px; padding: 0.5em;">
        <!-- Uso de la interpolación de estilo para aplicar el color de fondo dinámico -->
        <div :style="{ backgroundColor: item.color }">
          <span>{{ item.icon }}</span>
          <!-- Enlace de cantidad con v-model -->
          <input v-model.number="item.quantity" style="width: 25px;" type="text" placeholder="cantidad">
          <!-- Cálculo total en función de la cantidad y el precio -->
          <span>{{ (item.quantity * item.price).toFixed(2) }}</span>
        </div>
      </div>


      <div style="background-color: red; border-radius: 5px; width: 70px;">
        d
      </div>

    </div>

    <hr>

    <div>
      <span>Total: {{ Object.values(items).reduce((acc, item) => acc + item.quantity * item.price, 0) }}</span>
    </div>
  </div>
</template>

<script>
import { fastFoodItems } from './fastFoodItem';

export default {
  data() {
    const items = {};

    fastFoodItems.forEach(item => {
      items[item.name] = {
        quantity: 0,
        price: item.price,
        icon: item.icon,
        color: item.color
      };
    });

    return { items };
  },

  methods: {
    
  },
}

</script>

<style scoped>
 h1{
   color: red;
   text-align:center; 
 }

 
</style>