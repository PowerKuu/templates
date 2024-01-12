<script setup lang="ts">
const props = withDefaults(defineProps<{
    background?: string
    color?: string
    border?: string

    arrow?: boolean
}>(), {
    background: "var(--primary)",
    color: "var(--background)",
    arrow: true
})

const borderCSS = computed(() => {
    return `var(--border-width) solid ${props.border || props.background}`
})
</script>

<template>
    <button
        :style="{
            background: props.background,
            border: borderCSS
        }"
    >
        <SystemP class="text" :style="{
            color: props.color
        }">
            <slot></slot>
        </SystemP>

        <Icon name="ic:baseline-keyboard-arrow-right" size="1.4rem" :color="color"></Icon>
    </button>
</template>

<style scoped lang="scss">
button {
    border-radius: 10px;
    padding: 0 1.5em;
    height: var(--normal-height);

    display: flex;
    flex-direction: row;

    align-items: center;

    gap: 0.225rem;

    cursor: pointer;

    transition: all 0.2s ease-in-out;

    .text {
        font-weight: 500;
    }

    &:hover {
        opacity: 0.8;
    }

    &[disabled] {
        opacity: 0.5;
        cursor: not-allowed;
    }
}
</style>