<template>
    <b-table :data="clients" :columns="columns"></b-table>
</template>

<script>
    export default {
        props: {
          clients: Array,
        },
data() {
return {
columns: [
{
field: 'client.id',
label: 'ID',
},
{
field: 'client.clientName',
label: 'Client Name',
searchable: true,
},
{
field: 'last_name',
label: 'Last Name',
searchable: true,
},
{
field: 'date',
label: 'Date',
centered: true
},
{
field: 'gender',
label: 'Gender',
}
]
}
}
}
</script>