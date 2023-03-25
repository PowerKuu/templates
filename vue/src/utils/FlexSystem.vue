<script setup lang="ts">
interface Props {
    tag?: string
    gap?: string,
    direction?: "row" | "row-reverse" | "column" | "column-reverse",
    align?: "start" | "center" | "end" | "stretch",
    justify?: "start" | "center" | "end" | "stretch" | "space-around" | "space-between" | "space-evenly"
    alignSelf?: "start" | "center" | "end" | "stretch"
    justifySelf?: "start" | "center" | "end" | "stretch" | "space-around" | "space-between" | "space-evenly"
    grow?: string,
    
    height?: string
    width?: string
}
const props = defineProps<Props>()
const deafultProps = {
    tag: "div",
    direction: "row",
    gap: 0,
    align: "start",
    justify: "start",
    alignSelf: "auto",
    justifySelf: "auto",
    grow: "0 1 auto",
    height: "auto",
    width: "auto"
}
function mergeProps(props1:any, props2:any) {
    const mergedProps = props1
    for (const [key, value]of Object.entries(props2)) {
        if (!value)  continue
        mergedProps[key] = value
    }
    return mergedProps
}
const mergedProps = mergeProps(deafultProps, props)
</script>

<template>
<component :is="mergedProps.tag" :style="{
    display: 'flex',
    flexDirection: mergedProps.direction,
    gap: mergedProps.gap + 'rem',
    alignItems: mergedProps.align,
    justifyContent: mergedProps.justify,
    flex: mergedProps.grow,
    alignSelf: mergedProps.alignSelf,
    justifySelf: mergedProps.justifySelf,
    height: mergedProps.height,
    width: mergedProps.width
}">
    <slot></slot>
</component>
</template>


<style>
html {
    font-size: 20px;
}

body, html {
    margin: 0;
    padding: 0;
    overflow-x: hidden;
    position: relative;
}
* {
    margin: 0;
    box-sizing: border-box;
}
p, a {
    font-size: 1rem;
}
a {
    color: inherit;
    text-decoration: underline;
}
input, textarea {
    outline: none;
    border: none;
    border: 1px solid #C0C0C0;
    font-family: inherit;
    padding: 0.5rem 0.7rem 0.5rem 0.7rem;
    font-size: 1rem;
    resize: none; 
    width: 100%;
    padding: 0.6rem 1rem;
}
button {
    outline: none;
    border: none;
    border: 1px solid #C0C0C0;
    padding: 0.5rem 0.7rem 0.5rem 0.7rem;
    font-size: 1rem;
    font-family: inherit;
    resize: none; 
    padding: 0.6rem 2rem;
}
button:hover {
    cursor: pointer;
}
</style>