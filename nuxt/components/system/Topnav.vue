<script setup lang="ts">

</script>

<template>
    <SystemFlex class="navbar" align="center" justify="space-between">
        <slot name="left"></slot>
        <slot name="right"></slot>
    </SystemFlex>
</template>

<style scoped lang="scss">
.navbar {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;

    z-index: 10;

    padding: 1rem var(--page-padding);

    background: var(--background);
    
    border-bottom: var(--border-width) solid var(--neutral);
}
</style>