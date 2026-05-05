<template>
  <div class="container">
    <h1 class="text-center mb-4">Update Employee Records</h1>
    
    <!-- Table Wrapper: scrollable on small devices -->
    <div class="table-responsive shadow-sm mb-4">
      <table class="table table-bordered table-striped table-hover text-center mb-0">
        <thead class="table-warning">
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
          <!-- List of employees with an Edit button -->
          <tr v-for="item in list" :key="item.id">
            <td>{{ item.id }}</td>
            <td>{{ item.name }}</td>
            <td>{{ item.designation }}</td>
            <td>{{ item.department }}</td>
            <td>{{ item.salary }}</td>
            <td>
              <button class="btn btn-warning btn-sm fw-bold" @click="editItem(item)">
                ✏️ Edit
              </button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>

    <!-- Edit Section: Only visible when an employee is selected -->
    <div class="row justify-content-center" v-if="editData.id">
      <div class="col-12 col-md-8 col-lg-6">
        <div class="card shadow p-4 border-0 bg-light">
          <h5 class="mb-3 text-center">Edit Employee Details</h5>
          
          <div class="mb-3">
            <label class="form-label fw-bold">Name</label>
            <input class="form-control" v-model="editData.name" />
          </div>

          <div class="mb-3">
            <label class="form-label fw-bold">Designation</label>
            <input class="form-control" v-model="editData.designation" />
          </div>

          <div class="mb-3">
            <label class="form-label fw-bold">Department</label>
            <input class="form-control" v-model="editData.department" />
          </div>

          <div class="mb-3">
            <label class="form-label fw-bold">Salary</label>
            <input class="form-control" type="number" v-model="editData.salary" />
          </div>

          <div class="d-flex gap-2">
            <button class="btn btn-success flex-grow-1 fw-bold" @click="updateData">
              💾 Save Changes
            </button>
            <button class="btn btn-secondary fw-bold" @click="cancelEdit">
              Cancel
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "UpdateEmployee",
  data() {
    return {
      // MockAPI Endpoint
      apiURL: "https://69f8cc42f7044aa0103e80c0.mockapi.io/assig-2",
      // List of employees fetched from server
      list: [],
      // Data of the employee currently being edited
      editData: {
        id: null,
        name: "",
        designation: "",
        department: "",
        salary: 0,
      },
    };
  },
  methods: {
    /**
     * Fetch all employees from the API
     */
    async fetchData() {
      try {
        const resp = await axios.get(this.apiURL);
        this.list = resp.data;
      } catch (err) {
        console.error("Error fetching data:", err);
      }
    },
    /**
     * Load an employee's data into the edit form
     * @param {Object} item - Employee object to edit
     */
    editItem(item) {
      this.editData = { ...item };
      // Scroll to form on small screens
      setTimeout(() => {
        window.scrollTo({ top: document.body.scrollHeight, behavior: 'smooth' });
      }, 100);
    },
    /**
     * Clear edit data and hide the form
     */
    cancelEdit() {
      this.editData = { id: null, name: "", designation: "", department: "", salary: 0 };
    },
    /**
     * Send PUT request to update employee data
     */
    async updateData() {
      try {
        await axios.put(`${this.apiURL}/${this.editData.id}`, this.editData);
        alert("Employee updated successfully!");
        this.fetchData(); // Refresh list
        this.cancelEdit(); // Hide form
      } catch (err) {
        console.error("Error updating employee:", err);
        alert("Failed to update employee.");
      }
    },
  },
  mounted() {
    this.fetchData();
  },
};
</script>
