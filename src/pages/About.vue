<template>
  <div class="pa-8">
    <div class="text-center">
      <img class="mb-3" :src="HorizontalLogo" width="350" />
      <p class="mb-5">A Tauri based GUI app that upscale images using Real-ESRGAN model.</p>
      <v-divider class="mb-5" />
      <div class="text-left">
        <p><strong>Version: </strong>v{{ appVersion }}</p>
        <p><strong>Author: </strong>{{ 'PixMiller <hello@pixmiller.com>' }}</p>
        <p><strong>Web: </strong>{{ 'https://pixmiller.com' }}</p>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { invoke } from "@tauri-apps/api/tauri";
import { onMounted, ref } from "vue";
import HorizontalLogo from '@/assets/pixmiller-horizontal.png';

const appVersion = ref("");

onMounted(async () => {
  const result: string = await invoke("get_version");
  appVersion.value = result;
});
</script>
