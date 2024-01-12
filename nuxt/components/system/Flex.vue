<script setup lang="ts">
interface Props {
    tag: string
    gap: string,
    direction: "row" | "row-reverse" | "column" | "column-reverse",
    align: "start" | "center" | "end" | "stretch",
    justify: "start" | "center" | "end" | "stretch" | "space-around" | "space-between" | "space-evenly"
    alignSelf: "start" | "center" | "end" | "stretch" | "auto"
    justifySelf: "start" | "center" | "end" | "stretch" | "space-around" | "space-between" | "space-evenly" | "auto"
    grow: string,
    
    height: string
    width: string
}

const props = defineProps<Partial<Props>>()

const deafultProps: Props = {
    tag: "div",
    direction: "row",
    gap: "0",
    align: "stretch",
    justify: "stretch",
    alignSelf: "auto",
    justifySelf: "auto",
    grow: "0 1 auto",
    height: "auto",
    width: "auto"
}

function mergeProps(props1:Props, props2: Partial<Props>): Props  {
    const mergedProps = props1
    for (const [key, value] of Object.entries(props2)) {
        if (!value)  continue
        (mergedProps as any)[key] = value
    }

    return mergedProps
}

const mergedProps = computed(() => {
    return mergeProps(deafultProps, props)
})

const style = computed(() => {
    return {
        "--flex-direction": mergedProps.value.direction,
        "--gap": mergedProps.value.gap,
        "--align-items": mergedProps.value.align,
        "--justify-content": mergedProps.value.justify,
        "--flex": mergedProps.value.grow,
        "--align-self": mergedProps.value.alignSelf,
        "--justify-self": mergedProps.value.justifySelf,
        "--height": mergedProps.value.height,
        "--width": mergedProps.value.width,
    }
})
</script>

<template>
    <component class="flex" :is="mergedProps.tag" :style="style">
        <slot></slot>
    </component>
</template>

<style scoped>
.flex {
    display: flex;
    flex-direction: var(--flex-direction);
    gap: var(--gap);
    align-items: var(--align-items);
    justify-content: var(--justify-content);
    flex: var(--flex);
    align-self: var(--align-self);
    justify-self: var(--justify-self);
    height: var(--height);
    width: var(--width);
}
</style>