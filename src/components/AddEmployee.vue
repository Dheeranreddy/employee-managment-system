<template>
  <div class="container">
    <h1 class="text-center mb-4">Add New Employee</h1>
    
    <div class="row justify-content-center">
      <!-- Responsive Column: Full width on mobile, half width on medium+ screens -->
      <div class="col-12 col-md-8 col-lg-6">
        <div class="card shadow p-4 border-0">
          <form @submit.prevent="postData">
            
            <!-- Employee Name Field -->
            <div class="mb-3">
              <label class="form-label fw-bold">Full Name</label>
              <input
                type="text"
                class="form-control"
                placeholder="Enter name"
                v-model="posts.name"
                required
              />
            </div>

            <!-- Designation Field -->
            <div class="mb-3">
              <label class="form-label fw-bold">Designation</label>
              <input
                type="text"
                class="form-control"
                placeholder="Enter designation"
                v-model="posts.designation"
                required
              />
            </div>

            <!-- Department Field -->
            <div class="mb-3">
              <label class="form-label fw-bold">Department</label>
              <input
                type="text"
                class="form-control"
                placeholder="Enter department"
                v-model="posts.department"
                required
              />
            </div>

            <!-- Salary Field -->
            <div class="mb-3">
              <label class="form-label fw-bold">Salary</label>
              <input
                type="number"
                class="form-control"
                placeholder="Enter salary"
                v-model="posts.salary"
                required
              />
            </div>

            <!-- Submit Button -->
            <button type="submit" class="btn btn-primary w-100 fw-bold">
              🚀 Add Employee
            </button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "AddEmployee",
  data() {
    return {
      // MockAPI Endpoint
      apiURL: "https://69f8cc42f7044aa0103e80c0.mockapi.io/assig-2",
      // Object to store form input data
      posts: {
        name: null,
        designation: null,
        department: null,
        salary: 0,
      },
    };
  },
  methods: {
    /**
     * Sends a POST request to create a new employee
     */
    async postData() {
      try {
        const res = await axios.post(this.apiURL, this.posts);
        console.log("Success:", res.data);
        alert("Employee added successfully!");
        
        // Reset form after successful submission
        this.posts = {
          name: "",
          designation: "",
          department: "",
          salary: 0,
        };
      } catch (err) {
        console.error("Error creating employee:", err);
        alert("Failed to add employee.");
      }
    },
  },
};
</script>
