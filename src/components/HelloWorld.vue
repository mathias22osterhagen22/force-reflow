<script setup>
import { ref } from "vue";

defineProps({
  msg: String,
});

function getNewA() {
  let a = [];
  for (let i = 0; i < 25000; i++) {
    a.push({ id: i, value: Math.random() });
  }
  return a;
}

let myarray = ref(getNewA());
setInterval(() => {
  myarray.value = getNewA();
}, 1000);
</script>

<template>
  <h1>{{ msg }}</h1>

  <table class="w-full">
    <thead>
      <tr>
        <th>#</th>
        <th>Value</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="item of myarray">
        <td>{{ item.id }}</td>
        <td>{{ item.value }}</td>
      </tr>
    </tbody>
  </table>
</template>
