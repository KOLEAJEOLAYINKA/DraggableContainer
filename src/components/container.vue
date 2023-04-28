<template>
    <div class="container"
         @dragover.prevent
         @drop="dropHandler"
         >
      <span class="label">Container Box</span>
  
      <Content />
  
    </div>
  </template>
  
  <script lang='ts' setup>
  import Content from './Content.vue';
  
  export  {
    components: {
      Content
    },
    methods: {
      dropHandler(event) {
        const containerBox = event.target;
        const offsetX = event.offsetX;
        const offsetY = event.offsetY;
        containerBox.style.left = `${offsetX}px`;
        containerBox.style.top = `${offsetY}px`;
      }
    }
  }
  </script>
  
  <style lang='postcss' scoped>
  .container {
    @apply w-96 h-80 bg-gray-300 flex items-center justify-center relative;
  }
  
  .label {
    @apply absolute -top-3 px-3 left-0 bg-gray-300 text-black text-xs;
  }
  </style>
  