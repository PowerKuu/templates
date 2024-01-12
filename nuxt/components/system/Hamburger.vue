<script setup lang="ts">
const showMenu = ref(false)
</script>

<template>
    <Icon @click="showMenu = !showMenu" name="solar:hamburger-menu-linear" class="hamburger"></Icon>

    <SystemOverlay @click="showMenu = false" v-if="showMenu"></SystemOverlay>

    <SystemFlex v-if="showMenu" class="hamburger-menu" gap="1.5rem" direction="column">
        <Icon @click="showMenu = !showMenu" color="var(--text)" name="akar-icons:cross" class="cross"></Icon>
        
        <SystemFlex gap="1rem" direction="column">
            <slot></slot>
        </SystemFlex>
    </SystemFlex>
</template>

<style scoped lang="scss">
.hamburger {
    width: 2rem;
    height: 2rem;
    cursor: pointer;
}

.hamburger-menu {
    position: fixed;
    top: 0;
    left: 0;
    width: max(40vw, 500px);
    height: 100%;

    padding: 5rem var(--page-padding);

    background: var(--background);
    backdrop-filter: blur(5px);
}

.cross {
    width: 1.25rem;
    height: 1.25rem;
    cursor: pointer;
}
</style>