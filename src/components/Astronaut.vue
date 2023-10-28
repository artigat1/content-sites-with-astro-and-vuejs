<template>
    <span id="rotateMe"
          ref="el">🧑‍🚀</span>
</template>

<script lang="ts" setup>
    import {useMouse} from '@vueuse/core'
    import {computed, ref} from 'vue';
    
    const {x, y} = useMouse();
    const el = ref<HTMLElement>();
    const cssRotate = computed(() => {
        if (!el.value) return '';
        
        const rect = el.value.getBoundingClientRect();
        const centerX = rect.left + rect.width / 2;
        const centerY = rect.top + rect.height / 2;
    
        const deltaX = x.value - centerX;
        const deltaY = y.value - centerY;
    
        const rad = Math.atan2(deltaY, deltaX);
        const deg = rad * (180 / Math.PI) + 90;
    
        return `rotate(${deg}deg)`;
    })
    
</script>

<style scoped>
    #rotateMe {
        transform-origin: center center;
        transform: v-bind(cssRotate);
        display: inline-block;
    }
</style>