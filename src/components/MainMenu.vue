<script setup lang="ts">
import MainMenuItem from './MainMenuItem.vue';
</script>

<template>
<div class="absolute bottom-[20vh] left-[50px]">
    <MainMenuItem :title="'Play'" :sub-title="'Hit the field'" />
    <MainMenuItem :title="'Item Shop'" :sub-title="'Unlock New Contnent'" :item-shop-styling="true" />
    <MainMenuItem :title="'Rocket Pass'" :sub-title="'View your Rocket Pass content'"/>
    <MainMenuItem :title="'Garage'" :sub-title="'View customiztion options'"/>
    <MainMenuItem :title="'Profile'" :sub-title="'View stats and records'"/>
    <MainMenuItem :title="'Settings'" :sub-title="'Modify your settings'"/>
    <MainMenuItem :title="'Quit'" :sub-title="'Exit Rocket League'"/>
</div>
</template>