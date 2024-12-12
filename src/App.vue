<template>
  <div>
    <h1>Csapat List</h1>
    <ul>
      <li v-for="csapat in csapatList" :key="csapat.csapatId">
        {{ csapat.csapatNev }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      csapatList: [], // To store the list of Csapat
    };
  },
  mounted() {
    this.getCsapat(); // Call the API when the component is mounted
  },
  methods: {
    async getCsapat() {
      try {
        const response = await axios.get('http://localhost:5163/api/Csapat');
        this.csapatList = response.data; // Store the response data in csapatList
      } catch (error) {
        console.error('Error fetching data:', error);
      }
    },
  },
};
</script>

<style>
/* Add your styles here */
</style>
