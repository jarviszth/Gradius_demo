<template>
  <v-card>
  <v-card-title>
    <h2>รายชื่อผู้ใช้งาน</h2>
    <v-spacer></v-spacer>
    <v-btn color="primary"  small dark class="mt-4" v-on="on"><v-icon>fas fa-user-plus</v-icon> เพิ่มผู้ใช้งาน</v-btn>
    <v-text-field
      v-model="search"
      append-icon="mdi-magnify"
      label="ค้นหา"
      single-line
      hide-details
    ></v-text-field>
  </v-card-title>
  <v-data-table
    class="table"
    :headers="headers"
    :items="users.dataList"
    :rows-per-page-items="[5, 10, 25, 50 ,100]">
    <template slot="items" slot-scope="props">
      <td class="text-xs-left">{{ props.item.username }}</td>
      <td class="text-xs-left">{{ props.item.fname }}</td>
      <td class="text-xs-left">{{ props.item.lname }}</td>
      <td class="text-xs-left">{{ props.item.email }}</td>
      <td class="text-xs-left"><v-icon small class="mr-2" @click="editItem(item)">edit</v-icon><v-icon small @click="deleteItem(item)">delete</v-icon></td>
    </template>
  </v-data-table>
    </v-card>
</template>

<script>

  export default {
    data() {
      return {
        users: [],
        headers: [
          {
            text: 'ชื่อผู้ใช้งาน',
            value: 'username',
            align: 'left',
            sortable: true
          },
          {
            text: 'ชื่อจริง',
            value: 'fname',
            align: 'left',
            sortable: true
          },
          {
            text: 'นามสกุล',
            value: 'lname',
            align: 'left',
            sortable: true
          },
          {
            text: 'อีเมล',
            value: 'lname',
            align: 'left',
            sortable: true
          },
          {
            text: 'จัดการ',
            value: '#',
            align: 'left',
            sortable: false
          }
        ]
      }
    },

    methods: {

    },

    created() {
      const vm = this;

      vm.axios.get('http://localhost/gradius_api/radcheckList').then(response => {
        var result = response && response.data;

        vm.users = result;
        console.log(result.dataList);
      });
    }
  }
</script>

<style>
  .table {
    border-radius: 3px;
    background-clip: border-box;
    border: 1px solid rgba(0, 0, 0, 0.125);
    box-shadow: 1px 1px 1px 1px rgba(0, 0, 0, 0.21);
    background-color: transparent;
  }
</style>
