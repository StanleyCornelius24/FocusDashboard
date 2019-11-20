<template>
  <div id="app" class="container">
    <h1>Monthly Clients</h1>
    <retainer-client-table-bue :retainerClients="retainerClients" />
    <h1>Project Clients</h1>
    <project-client-table-bue :projectClients="projectClients" />
  </div>
</template>

<script>
import RetainerClientTableBue from '@/components/RetainerClientTableBue.vue'
import ProjectClientTableBue from '@/components/ProjectClientTableBue.vue'

export default {
  name: 'app',
  components: {
    RetainerClientTableBue,
    ProjectClientTableBue,
  },
  
  data() {
    return {
      retainerClients: [],
      projectClients: []
    }
  },

  mounted() {
    this.getRetainerClients(),
    this.getProjectClients()
  },


  methods: {

    async getRetainerClients() {
      try {
        const response = await fetch('https://www.focusonlinetravel.co.za/clientBudgets.php?type=retainer')
        //const response = await fetch('https://jsonplaceholder.typicode.com/users')
        const data = await response.json()
        this.retainerClients = data
      } catch (error) {
        //console.error(error)
      }
    },

    async getProjectClients() {
      try {
        const response = await fetch('https://www.focusonlinetravel.co.za/clientBudgets.php?type=projects')
        //const response = await fetch('https://jsonplaceholder.typicode.com/users')
        const data = await response.json()
        this.projectClients = data
      } catch (error) {
        //console.error(error)
      }
    }

  }
}
</script>

<style scoped></style>