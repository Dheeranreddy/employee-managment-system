<template>
  <div id="app">
    <!-- Navbar: Responsive Bootstrap navigation bar -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-primary shadow-sm">
      <div class="container">
        <!-- Brand Name -->
        <span class="navbar-brand fw-bold">👥 Employee Management</span>

        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarNav"
          aria-controls="navbarNav"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>

        <!-- Navbar Links -->
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav ms-auto gap-2 mt-2 mt-lg-0">
            <li class="nav-item">
              <button
                class="btn btn-light btn-sm w-100"
                @click="setView('add')"
              >
                ➕ Add Employee
              </button>
            </li>
            <li class="nav-item">
              <button
                class="btn btn-light btn-sm w-100"
                @click="setView('view')"
              >
                📋 View List
              </button>
            </li>
            <li class="nav-item">
              <button
                class="btn btn-light btn-sm w-100"
                @click="setView('update')"
              >
                ✏️ Update Details
              </button>
            </li>
            <li class="nav-item">
              <button
                class="btn btn-light btn-sm w-100"
                @click="setView('delete')"
              >
                🗑️ Delete Records
              </button>
            </li>
          </ul>
        </div>
      </div>
    </nav>

    <!-- Main Content Area: Renders the selected component -->
    <main class="container py-4">
      <AddEmployee v-if="currentView === 'add'" />
      <ViewEmployee v-if="currentView === 'view'" />
      <UpdateEmployee v-if="currentView === 'update'" />
      <DeleteEmployee v-if="currentView === 'delete'" />
    </main>
  </div>
</template>

<script>
// Importing CRUD components
import AddEmployee from "./components/AddEmployee.vue";
import ViewEmployee from "./components/ViewEmployee.vue";
import UpdateEmployee from "./components/UpdateEmployee.vue";
import DeleteEmployee from "./components/DeleteEmployee.vue";

export default {
  name: "App",
  components: {
    AddEmployee,
    ViewEmployee,
    UpdateEmployee,
    DeleteEmployee,
  },
  data() {
    return {
      // Default view is the list of employees
      currentView: "view",
    };
  },
  methods: {
    /**
     * Changes the current visible component
     * @param {string} view - The name of the component to display
     */
    setView(view) {
      this.currentView = view;
      // Close mobile menu after selection (optional improvement)
      const navbarCollapse = document.getElementById("navbarNav");
      if (navbarCollapse.classList.contains("show")) {
        navbarCollapse.classList.remove("show");
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
