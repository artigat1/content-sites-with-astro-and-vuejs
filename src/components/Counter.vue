<template>
    <slot name="top"></slot>
    
    <button @click="$event => counter++">{{counter}}</button>
    
    <slot name="bottom"></slot>
</template>

<script setup lang="ts">
    import {ref} from 'vue'
    
    const props = defineProps({
        initialCount: Number,
    })
    const counter = ref<number>(props.initialCount ?? 0)
</script>