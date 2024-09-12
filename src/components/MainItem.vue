<script setup lang="ts">
import { ref } from 'vue';
import MobileGame from './main-item/MobileGame.vue';
import Joki from './main-item/Joki.vue';
import Pulsa from './main-item/Pulsa.vue';
import Voucher from './main-item/Voucher.vue';
import AppPremium from './main-item/AppPremium.vue';

// Daftar items dengan komponen yang akan dirender
const items = [
    {
        id: 0,
        title: 'Mobile Game',
        component: MobileGame
    },
    {
        id: 1,
        title: 'Jasa Joki',
        component: Joki
    },
    {
        id: 2,
        title: 'Pulsa',
        component: Pulsa
    },
    {
        id: 3,
        title: 'Voucher',
        component: Voucher
    },
    {
        id: 4,
        title: 'App Premium',
        component: AppPremium
    },
]

// State untuk menyimpan item yang dipilih
const selectedItem = ref(items[0]);

// Fungsi untuk mengatur item yang dipilih
const selectItem = (item: any) => {
    selectedItem.value = item;
};
</script>

<template>
  <div class="rounded-md p-2 bg-white dark:border dark:border-gray-700 mt-2 dark:bg-gray-800">
    <div class="flex flex-wrap border-b border-gray-200 dark:border-gray-700">
      <!-- List menu -->
      <ul class="flex flex-wrap text-sm font-medium text-center text-gray-500 dark:text-gray-400">
        <li v-for="item in items" :key="item.id" class="mr-2">
          <a
            href="#"
            class="inline-flex items-center justify-center p-4 text-gray-400 border-b-2 rounded-t-lg hover:text-blue-600 hover:border-blue-600 dark:hover:text-gray-300 group"
            :class="{'text-blue-600 border-blue-600': selectedItem.id === item.id}"
            @click.prevent="selectItem(item)"
          >
            {{ item.title }}
          </a>
        </li>
      </ul>
    </div>

    <!-- Menampilkan komponen berdasarkan item yang dipilih -->
    <div v-if="selectedItem.component" class="mt-4">
      <component :is="selectedItem.component" />
    </div>
  </div>
</template>