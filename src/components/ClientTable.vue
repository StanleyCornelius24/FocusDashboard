<template>
  <div id="client-table">
    <p v-if="clients.length < 1" class="empty-table">
      No clients
    </p>
    <table v-else>
      <thead>
        <tr>
          <th>Client name</th>
          <th>Project</th>
          <th>Budget (hours)</th>
          <th>Spent (hours)</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="client in clients" :key="client.id">
          <td>{{ client.clientName }}</td>
          <td>{{ client.projectName }}</td>
          <td>{{ client.projectBudget }}</td>
          <td v-if="client.projectTime < client.projectBudget" style="background-color:green; color: white;">{{ client.projectTime }}</td>
          <td v-else style="background-color:red; color: white">{{ client.projectTime }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
  export default {
    name: 'client-table',
    props: {
      clients: Array,
    },
    data() {
      return {
        editing: null,
      }
    }
  }
</script>

<style scoped>
button {
    margin: 0 0.5rem 0 0;
  }
</style>