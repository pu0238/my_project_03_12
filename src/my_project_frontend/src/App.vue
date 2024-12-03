<script setup>
import { ref } from 'vue';
// https://api.nbp.pl/api/exchangerates/tables/A/?format=json

const rates = ref([])
fetch("https://api.nbp.pl/api/exchangerates/tables/A/?format=json").then(async (res) => {
  const jsonData = await res.json()
  console.log(jsonData)

  rates.value = jsonData[0].rates
})
</script>

<template>
  <main>
  <table>
    <tr>
      <th>Kod</th>
      <th>Nazwa waluty</th>
      <th>Kurs</th>
    </tr>
    <tr v-for="rate in rates">
      <td>{{  rate.code }}</td>
      <td>{{  rate.currency }}</td>
      <td>{{  rate.mid }}</td>
    </tr>
  </table>
  </main>
</template>
