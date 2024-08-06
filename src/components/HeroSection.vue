<script setup lang="ts">
    import { onMounted, ref } from 'vue'
    const props = defineProps({
        title: {
            type: String,
            required: false,
            default: 'Hero Section'
        },
        content: {
            type: String,
            required: false,
            default: 'Some text here'
        },
        width: {
            type: String,
            required: false,
            default: '70dvw'
        },
        height: {
            type: String,
            required: false,
            default: '40dvh'
        },
        backgroundColor: {
            type: String,
            required: false,
            default: '#f0f0f0'
        },
        color: {
            type: String,
            required: false,
            default: '#000'
        },
        shadow: {
            type: String,
            required: false,
            default: 'rgba(0, 0, 0, 0.1)'
        }
    });


    const hero = ref(null)
    const heroHeader = ref(null)
    const heroContent = ref(null)
    const width = ref(props.width)
    const height = ref(props.height)
    const backgroundColor = ref(props.backgroundColor)
    const color = ref(props.color)
    const shadow = ref(props.shadow)

    const handleMouseEnter = () => {
        //transform scale to 1.1 and expand box shadow colored to blue
        hero.value.style.transform = 'scale(1.03)'
        hero.value.style.boxShadow = '0 0 10px rgba(0, 0, 255, 0.1)'
        hero.value.style.transition = 'all 0.5s'
    }

    const handleMouseLeave = () => {
        //transform scale to 1 and box shadow colored to black
        hero.value.style.transform = 'scale(1)'
        hero.value.style.boxShadow = shadow.value
        hero.value.style.transition = 'all 0.5s'
    }

    onMounted(() => {
        if (hero.value && heroHeader.value) {
            hero.value.style.width = width.value
            hero.value.style.height = height.value
            hero.value.style.borderRadius = '10px'
            hero.value.style.border = '1px solid #fff'
            hero.value.style.boxShadow = shadow.value
            heroContent.value.style.width = width.value
            heroContent.value.style.backgroundColor = backgroundColor.value
            heroContent.value.style.color = color.value
        }
    })
</script>
<template>
    <div ref="hero" class="hero"
        @mouseenter="handleMouseEnter"
        @mouseleave="handleMouseLeave"
    >
        <div ref="heroHeader" class="hero_header">
            <h1>Hero Section</h1>
            <p>Some text here</p>
        </div>
        <div ref="heroContent" class="hero_content">
            <p>Some more text here</p>
        </div>
    </div>
</template>
<style scoped>
    .hero {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    .hero_header {
        text-align: center;
    }

    .hero_content {
        text-align: center;
    }

</style>
