<script setup lang="ts">
const props = withDefaults(defineProps<{
    width?: string
    height?: string
}>(), {
    width: "fit-content",
    height: "var(--normal-height)"
})
</script>

<template>
    <img 
        :style="{
            width: props.width,
            height: props.height
        }" 
        
        src="/icons/logo.svg" 
        alt="Logo"
        class="logo"
    />
</template>