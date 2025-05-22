<script setup lang="ts">
defineProps<{
    title: string;
    subTitle?: string;
    itemShopStyling?: boolean;
}>();
</script>

<template>
<div :class="`menu-item flex items-center bg-black text-white text-3xl rounded px-4 py-1 w-[18.75vw] h-[64px] mb-1 skew-x-[-10deg] electrolize-regular cursor-pointer ${itemShopStyling ? 'item-shop' : 'opacity-95'}`">
    <div :class="itemShopStyling ? 'item-shop-text' : ''">
        <div class="title-text uppercase transition-all duration-500">
            {{ title }}
        </div>
        <div class="sub-title-text uppercase text-base opacity-0">
            {{ subTitle }}
        </div>
    </div>
</div>
</template>

<style scoped>
.menu-item:hover {
    filter: drop-shadow(0px 0px 12px #C1E3EE);
    background: linear-gradient(90deg, #c3e4ef 10%, #d3eff9 60%) !important;
}

.item-shop:hover{
    filter: drop-shadow(0px 0px 12px #f4cf3e) !important;
    background: linear-gradient(90deg, #FFFFC6 10%, #FFFFE4 60%) !important;
}

.menu-item:hover .title-text {
    color: var(--menu-hover-text-color);
    transform: translateY(4px);
}

.menu-item:hover .sub-title-text {
    color: var(--menu-hover-text-color);
    opacity: 100;
    display: block;
    transition: ease-in-out .2s;
}

.menu-item:hover .item-shop-text .title-text {
    color: var(--item-shop-hover-text-color) !important;
}

.menu-item:hover .item-shop-text .sub-title-text {
    color: var(--item-shop-hover-text-color) !important;
}

.title-text{
    transform: translateY(12px);
}

.sub-title-text {
    transform: translateY(-2px);
    transition: all .2s;
}

.item-shop {
    background: linear-gradient(90deg, rgba(22,16,3,1) 10%, rgba(49,30,3,1) 60%);
}

.item-shop-text {
    color: var(--item-shop-text-color) !important;
}
</style>