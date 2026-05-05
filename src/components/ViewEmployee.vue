<template>
  <div class="container">
    <h1 class="text-center mb-4">Employee Directory</h1>
    
    <!-- Table Wrapper: Makes the table horizontally scrollable on small screens -->
    <div class="table-responsive shadow-sm">
      <table class="table table-bordered table-striped table-hover text-center mb-0">
        <thead class="table-primary">
          <tr>
            <th>ID</th>
            <th>Name</th>
            <th>Designation</th>
            <th>Department</th>
            <th>Salary</th>
          </tr>
        </thead>
        <tbody>
          <!-- Dynamic rendering of employee list -->
          <tr v-for="item in list" :key="item.id">
            <td>{{ item.id }}</td>
            <td>{{ item.name }}</td>
            <td>{{ item.designation }}</td>
            <td>{{ item.department }}</td>
            <td>{{ item.salary }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "ViewEmployee",
  data() {
    return {
      // MockAPI Endpoint
      apiURL: "https://69f8cc42f7044aa0103e80c0.mockapi.io/assig-2",
      // Array to store fetched employees
      list: [],
    };
  },
  mounted() {
    /**
     * Fetch all employees when the component is mounted
     */
    axios
      .get(this.apiURL)
      .then((resp) => {
        this.list = resp.data;
      })
      .catch((err) => {
        console.error("Error fetching employees:", err);
      });
  },
};
</script>
