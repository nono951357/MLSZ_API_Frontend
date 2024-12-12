<template>
  <div>
    <h1>Csapat List</h1>
    <ul>
      <li v-for="csapat in csapatList" :key="csapat.csapatId">{{ csapat.csapatNev }}</li>
      <li>Összesen: {{ csapatList.length }}</li>
      <button @click="fetchCsapatList">Újjra lekérdezés</button>
    </ul>
  </div>
</template>

<script>
import CsapatApi from './generated-client/src/api/CsapatApi';
import ApiClient from './generated-client/src/ApiClient';

export default {
  data() {
    return {
      csapatList: []
    };
  },
  created() {
    this.fetchCsapatList();
  },
  methods: {
    fetchCsapatList() {
      const apiClient = new ApiClient();
      const csapatApi = new CsapatApi(apiClient);
      
      csapatApi.apiCsapatGet((error, data) => {
        if (error) {
            console.error(error);
          } else {
            this.csapatList = data;
          }
        });
      }
    }
  };
</script>

<style>
/* Add your styles here */
</style>