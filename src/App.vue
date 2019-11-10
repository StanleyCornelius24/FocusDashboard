<template>
  <div id="app" class="container">
    <h1>Clients</h1>
    <client-table :clients="clients" />
  </div>
</template>

<script>
import ClientTable from '@/components/ClientTable.vue'

export default {
  name: 'app',
  components: {
    ClientTable,
  },
  
  data() {
    return {
      clients: [],
    }
  },

  mounted() {
    this.getClients()
  },

  /*
  computed: {
    orderedClients: function () {
      return clients.orderBy(this.clients, 'clientName')
    }
  },
  */

  methods: {

    async getClients() {
      try {
        const response = await fetch('https://www.focusonlinetravel.co.za/clientBudgets.php')
        //const response = await fetch('https://jsonplaceholder.typicode.com/users')
        const data = await response.json()
        this.clients = data
      } catch (error) {
        //console.error(error)
      }
    }

  }
}
</script>

<style scoped></style>