<script setup>
import { ref, onMounted } from 'vue';

const fundraisingData = ref(null);

const jsonData = ref([]);

onMounted(async () => {
  try {
    const response = await fetch('./assets/fundraisingTracker.json');
    if (!response.ok) {
      throw new Error('Network response was not ok');
    }
    jsonData.value = await response.json();
  } catch (error) {
    console.error('There was a problem fetching the JSON data:', error);
  }
});

</script>

<template>
  <div>
    <div class="border border-orange-900 bg-yellow-500 p-2 mx-auto w-96 flex justify-between mt-4">
      <div class="text-left font-bold">Current Fundraising Goal (CAD)</div>
      <div class="text-right font-bold">$275,000</div>
    </div>
    <table class="my-6 mx-auto w-96">
      <thead>
        <tr>
          <th class="px-3 border border-blue-900" colspan="2" style="background-color:#9FC5E8;">Funds Raised (as of {{ jsonData.Date }})</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in jsonData.Data" :key="item.Type" style="background-color: #E6EFFD;">
          <td class="px-3 border border-blue-900">{{ item.Type }}</td>
          <td class="text-right font-bold px-3 border border-blue-900">{{ item.Value }}</td>
        </tr>
      </tbody>
    </table>
</div>
</template>