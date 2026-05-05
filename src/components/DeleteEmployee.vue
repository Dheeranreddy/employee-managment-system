<template>
  <div class="container">
    <h1 class="text-center mb-4">Remove Employee Records</h1>
    
    <!-- Table Wrapper: Scrollable on small screens -->
    <div class="table-responsive shadow-sm">
      <table class="table table-bordered table-striped table-hover text-center mb-0">
        <thead class="table-danger">
          <tr>
            <th>ID</th>
            <th>Name</th>
            <th>Designation</th>
            <th>Department</th>
            <th>Salary</th>
            <th>Action</th>
          </tr>
        </thead>
        <tbody>
          <!-- Iterate through employees and provide a Delete option -->
          <tr v-for="item in list" :key="item.id">
            <td>{{ item.id }}</td>
            <td>{{ item.name }}</td>
            <td>{{ item.designation }}</td>
            <td>{{ item.department }}</td>
            <td>{{ item.salary }}</td>
            <td>
              <button class="btn btn-danger btn-sm fw-bold" @click="deleteItem(item.id)">
                🗑️ Delete
              </button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "DeleteEmployee",
  data() {
    return {
      // MockAPI Endpoint
      apiURL: "https://69f8cc42f7044aa0103e80c0.mockapi.io/assig-2",
      // List of employees to display
      list: [],
    };
  },
  methods: {
    /**
     * Fetch all employees to show in the deletion list
     */
    async fetchData() {
      try {
        const res = await axios.get(this.apiURL);
        this.list = res.data;
      } catch (err) {
        console.error("Fetch Error:", err);
      }
    },
    /**
     * Confirms and deletes an employee by ID
     * @param {number|string} id - The ID of the employee to delete
     */
    async deleteItem(id) {
      if (!confirm("Are you sure you want to delete this record?")) return;
      try {
        await axios.delete(`${this.apiURL}/${id}`);
        // Locally remove from list to update UI immediately
        this.list = this.list.filter((item) => item.id !== id);
        alert("Employee deleted successfully.");
      } catch (err) {
        console.error("Delete Error:", err);
        alert("Failed to delete record.");
      }
    },
  },
  mounted() {
    this.fetchData();
  },
};
</script>
