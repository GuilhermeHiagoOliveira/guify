
<template>
  <div class="guify">
    <SideBarLayout></SideBarLayout>
    <section>
      <HeaderLayout></HeaderLayout>
      <div class="music-section">
        <slot />
      </div>
    </section>
    <PlayerLayout></PlayerLayout>
  </div>
</template>

<script setup>
import SideBarLayout from "@/Layouts/SideBarLayout.vue";
import HeaderLayout from "@/Layouts/HeaderLayout.vue";
import PlayerLayout from "@/Layouts/PlayerLayout.vue";
import { Link } from "@inertiajs/inertia-vue3";
</script>