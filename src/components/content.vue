<template>
   <div class="content"
   draggable="true"
       @dragstart="dragStartHandler"
       @dragend="dragEndHandler"
       @dragover.prevent
       @drop="dropHandler"
   >
      <span class="label">Content Box</span>
   </div>
</template>

<script lang='ts' setup>
export  {
  data() {
    return {
      id: 'content-box-1'
    }
  },
  methods: {
    dragStartHandler(event) {
      event.dataTransfer.setData('text/plain', this.id);
    },
    dragEndHandler(event) {
      // Implement any cleanup logic here
    },
    dropHandler(event) {
      const containerBox = event.target;
      const contentBoxId = event.dataTransfer.getData('text/plain');
      const contentBox = document.getElementById(contentBoxId);
      containerBox.appendChild(contentBox);
    }
  }
}
</script>

<style lang='postcss' scoped>
   .content  {
      @apply bg-black h-24 w-36 relative;
   }
 .label {
       @apply absolute -top-3 px-3 left-0 bg-black text-white text-xs
    }
</style>

