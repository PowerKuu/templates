<script setup lang="ts">
const { theme } = defineProps<{
    theme: "white" | "color" | "none"
}>()
</script>

<template>
    <button class="button" :data-theme="theme">
        <slot></slot>
    </button>
</template>

<style scoped>
    .button {
        --padding-vertical: 0.65rem;
        --padding-horizontal: 1.6rem;
        appearance: none;
        border: none;
        padding: var(--padding-vertical) var(--padding-horizontal);
        cursor: pointer;
    }
    .button[data-theme="white"] {
        background-color: white;
        color: var(--color);
    }
    .button[data-theme="color"] {
        background-color: var(--color);
        color: white;
    }
    .button[data-theme="none"] {
        --border-size: 2px;
        
        padding: 
        calc(var(--padding-vertical) - var(--border-size)) 
        calc(var(--padding-horizontal) - var(--border-size));
        border: 2px solid var(--contrast);
        color: var(--contrast);
        background-color: white;
    }
</style>