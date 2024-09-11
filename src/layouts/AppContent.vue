<script setup lang="ts">

defineProps<{
  toggleButton: boolean;
  deviceType: 'mobile' | 'tablet' | 'desktop'
}>();
    
</script>

<template>
   <div :class="{
    'sm:ml-0': deviceType === 'mobile' && !toggleButton, 
    'ml-0': deviceType === 'desktop' && !toggleButton,
    'tablet-class': deviceType === 'tablet' && !toggleButton }" 
    class="p-4 bg-gray-100 dark:bg-gray-800 h-screen">
          <router-view />
   </div>
</template>

  
<style scoped>
  /* Additional styles can be added here */
</style>