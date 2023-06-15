<template>
  <router-link to="/main" class="text-3xl text-gray-700 font-semibold absolute left-24 top-10">Back</router-link>
  <div class="users">
    <div class="table">
      <h2 class="text-3xl text-gray-700 font-semibold mb-10 text-center">Students of Cambridge</h2>
      <EasyDataTable
        :headers="headers"
        :items="users"
        table-class-name="customize-table"
        
      />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import EasyDataTable from "vue3-easy-data-table";
import "vue3-easy-data-table/dist/style.css";

export default {
  components: { EasyDataTable },
  data() {
    return {
      api: "https://jsonplaceholder.typicode.com/users",
      users: [],
      headers: [
        { text: "ID", value: "id", sortable: true },
        { text: "Name", value: "name" },
        { text: "Username", value: "username" },
        { text: "Email", value: "email" },
        { text: "Phone Number", value: "phone" },
        { text: "City", value: "address.city" },
      ],
    };
  },
  methods: {
    async fetchUsers() {
      const users = await axios.get(this.api);
      this.users = users.data;
    },
  },
  mounted() {
    this.fetchUsers();
  },
};
</script>

<style>
.customize-table {
  --easy-table-border: 1px solid green;
  --easy-table-row-border: 1px solid green;

  --easy-table-header-font-size: 14px;
  --easy-table-header-height: 50px;
  --easy-table-header-font-color: #c1cad4;
  --easy-table-header-background-color: #111;

  --easy-table-header-item-padding: 10px 15px;

  --easy-table-body-even-row-font-color: #fff;
  --easy-table-body-even-row-background-color: #111;

  --easy-table-body-row-font-color: #c0c7d2;
  --easy-table-body-row-background-color: #111;
  --easy-table-body-row-height: 50px;
  --easy-table-body-row-font-size: 14px;

  --easy-table-body-row-hover-font-color: #2d3a4f;
  --easy-table-body-row-hover-background-color: #eee;

  --easy-table-body-item-padding: 10px 15px;

  --easy-table-footer-background-color: transparent;
  --easy-table-footer-font-color: transparent;
  --easy-table-footer-font-size: 1px;
  --easy-table-footer-padding: 0px;
  --easy-table-footer-height: 0px


  
}
.users {
  @apply min-h-screen flex justify-center items-center;
}
</style>
