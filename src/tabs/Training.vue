<script setup lang="ts">
   defineProps();
</script>

<template>
   <div class="training-ctn">
      <div class="side-area">Dd</div>
      <div class="barracks-area">B</div>
      <div class="inventory-area">C</div>
   </div>
</template>

<style lang="scss">
   @use '@/styles/global' as *;

   .training-ctn {
      width: 100%;
      height: 100%;
      padding: $s-1;

      display: grid;
      grid-area: 's s b b b' 's s b b b' 's s b b b' 'i i i i i' 'i i i i i';
   }

   .side-area {
      grid-area: s;
      background-color: blue;
      width: 100%;
      height: 100%;
   }
   .barracks-area {
      grid-area: b;
      background-color: red;
      width: 100%;
      height: 100%;
   }
   .inventory-area {
      grid-area: i;
      background-color: yellow;
      width: 100%;
      height: 100%;
   }
</style>
