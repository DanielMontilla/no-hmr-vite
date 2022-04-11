<script setup lang="ts">
   import { ref } from 'vue';
   import type { Tab } from './types';
   import { WINDOW_SIZE } from './CONST';
   import Label from './Tabs/Label.vue'; // TODO: interpolate values into 'main' styles
   import Training from './Tabs/Training.vue';

   let currentTab = ref<number>(0);
   const switchTab = (to: number): void => {
      currentTab.value = to;
   };

   // Starting tabs
   let tabs = ref<Tab[]>([
      {
         label: {
            title: 'training',
            onColor: 'hsl(219, 18%, 45%)',
            offColor: 'hsl(219, 35%, 40%)'
         }
      },
      {
         label: {
            title: 'explore',
            onColor: 'hsl(100, 18%, 40%)',
            offColor: 'hsl(100, 35%, 25%)'
         }
      },
      {
         label: {
            title: 'shop',
            onColor: 'hsl(250, 18%, 40%)',
            offColor: 'hsl(325, 35%, 25%)'
         }
      }
   ]);
</script>

<template>
   <main>
      <div class="temp-border">
         <div
            class="window"
            :style="{
               height: `${WINDOW_SIZE.HEIGHT}px`,
               width: `${WINDOW_SIZE.WIDTH}px`
            }"
         >
            <div class="tab-label-area">
               <Label
                  v-for="({ label }, i) in tabs"
                  :title="label.title"
                  :active="currentTab === i"
                  :onColor="label.onColor"
                  :offColor="label.offColor"
                  :callback="() => switchTab(i)"
               />
            </div>
            <div class="tab-page-area" :style="{ backgroundColor: tabs[currentTab].label.onColor }">
               <Training v-if="tabs[currentTab].label.title === 'training'" />
            </div>
         </div>
      </div>
   </main>
</template>

<style lang="scss">
   @use '@/styles/reset' as *;
   @use '@/styles/global' as *;

   main {
      @include flex-center;
      height: 100vh;
      width: 100vw;
      padding: $s-3;
   }

   .window {
      z-index: -1;
      background-color: $background;
      display: grid;
      grid-template-rows: $s-7 auto;
   }

   .temp-border {
      z-index: 1;
      box-sizing: content-box;
      border-style: solid;
      border-width: $s-2;
      border-radius: $s-0;
      border-color: $white-soft;
   }

   .tab-label-area {
      display: flex;
      align-items: end;
      background-color: $background;
   }

   .tab-page-area {
      @include flex-center;
      width: 100%;
      height: 100%;
      border-top-right-radius: $s-3;
   }
</style>
