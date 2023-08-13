<template>
  <div class="flex min-h-screen overflow-hidden bg-red-500">
    <!-- Sidebar -->
    <div
      class="flex-shrink-0 w-16 bg-gray-800 text-white flex flex-col items-center justify-center "
      :class="{ 'w-64': isSidebarExpanded }"
    >

      <!-- Sidebar Toggle Button -->
      <button
        class="text-white text-lg focus:outline-none"
        @click="toggleSidebar"
      >
        <svg
          v-if="isSidebarExpanded"
          class="w-6 h-6 fill-current"
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 24 24"
        >
          <!-- Sidebar Collapse Icon -->
          <path d="M4.927 19.071l-1.413-1.414L12 11.586l8.485 8.485-1.414 1.414L12 14.414l-7.071 7.071z" />
        </svg>
        <svg
          v-else
          class="w-6 h-6 fill-current"
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 24 24"
        >
          <!-- Sidebar Expand Icon -->
          <path
            d="M19 12H5m14 0h-2m2 0H5m14 0H3m16-8v14H5V4h14zM7 20h10m-10 0v-4M7 4v4m10-4v4"
          />
        </svg>
      </button>

      <!-- Sidebar Icons -->
      <div class="flex-1 mt-10">
        <ul>
          <li
            v-for="item in sidebarItems"
            :key="item.id"
            class="py-4 cursor-pointer"
          >
            <!-- Replace 'icon-class' with your own icon class -->
            <span class="w-6 h-6 mr-4 icon-class">
              <RouterLink :to="item.route" >
                ICON
            </RouterLink>
            </span>
            <span v-if="isSidebarExpanded">
              <RouterLink :to="item.route" >
                {{ item.label }}
            </RouterLink>
            
            </span>
          </li>
        </ul>
      </div>
    </div>

    <!-- Main content -->
    <div class="flex-grow bg-gray-700 ml-0 " :class="{ 'ml-0': isSidebarExpanded }">
      <!-- Content goes here -->
      <RouterView />
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { RouterLink, RouterView } from 'vue-router';

const isSidebarExpanded = ref(true);

const toggleSidebar = () => {
  isSidebarExpanded.value = !isSidebarExpanded.value;
};

const sidebarItems = [
  { id: 1, label: 'Home', iconClass: 'icon-home', route: '/' },
  { id: 2, label: 'About', iconClass: 'icon-about', route: '/about' },
  // Add more sidebar items as needed
];

</script>

<style scoped>
/* Add your own styles for the icons */
.icon-home {
  /* Replace with your own icon styles */
}

.icon-about {
  /* Replace with your own icon styles */
}
.flex-shrink-0 {
  transition: width 0.3s ease;
}
</style>
