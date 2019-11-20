<template>
    <b-table :data="retainerClients" :columns="columns" :default-sort-direction="asc"></b-table>
</template>

<script>
    export default {
        props: {
          retainerClients: Array,
        },
	data() {
		return {
			columns:[
				{
					field: 'clientName',
					label: 'Client',
					sortable: true,
					defaultSortDirection: 'asc',
					sortIcon: 'arrow-up',
					sortIconSize: 'is-small',
				},
				{
					field: 'projectName',
					label: 'Project',
					sortable: true,
				},
				{
					field: 'projectBudget',
					label: 'Budget',
				},
				{
					field: 'projectTime',
					label: 'Spent',
				}
			],
		}
	},
	methods: {
		isOverBudget: function(clients) {
			var i;
			for (i = 0; i < clients.length; i++) {
				if (clients.projectBudget > clients.projectTime) {
					return "green";
				} else {
					return "red";
				}
			}
			return "-";
		}
	}
}
</script>

<style>
    tr.is-info {
        background: #167df0;
        color: #fff;
    }
</style>