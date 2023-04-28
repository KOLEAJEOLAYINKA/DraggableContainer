<template>
   <div class="content"
       draggable="true"
       @dragstart="dragStartHandler"
       @dragend="dragEndHandler"
       @drop.prevent="drop"
       @dragover.prevent
   >
      <span class="label">Content Box</span>
   </div>
</template>

<script lang='ts' setup>
   const dragStartHandler = (event:DragEvent)=>{
      event.dataTransfer?.setData('site_id', 'content-box-1')
   }
   
   const dragEndHandler = (event:DragEvent)=>{
      // Implement any cleanup logic here
   }

   const drop = (event:DragEvent)=>{
      const containerBox = event.target as HTMLElement;
      const contentBoxId = event.dataTransfer?.getData('site_id');
      const contentBox = document.getElementById(contentBoxId!);
      containerBox.appendChild(contentBox!);
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
