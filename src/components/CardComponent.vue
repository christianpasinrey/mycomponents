<script setup lang="ts">
    import { onMounted, ref } from 'vue'
    const props = defineProps({
        title: {
            type: String,
            required: false,
            default: 'Card component'
        },
        subtitle: {
            type: String,
            required: false,
            default: 'Subtitle here'
        },
        content: {
            type: String,
            required: false,
            default: 'Some  content here'
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
        },
        justify: {
            type: String,
            required: false,
            default: 'center'
        },
        upperTitle: {
            type: Boolean,
            required: false,
            default: false
        },
        upperSubtitle: {
            type: Boolean,
            required: false,
        },
        upperContent: {
            type: Boolean,
            required: false,
        },
        htmlContent: {
            type: String,
            required: false,
        }
    });


    const card = ref(null)
    const cardHeader = ref(null)
    const cardTitle = ref(null)
    const cardSubtitle = ref(null)
    const cardContent = ref(null)
    const width = ref(props.width)
    const height = ref(props.height)
    const backgroundColor = ref(props.backgroundColor)
    const color = ref(props.color)
    const shadow = ref(props.shadow)
    const justiy = ref(props.justify)

    const handleMouseEnter = () => {
        //transform scale to 1.1 and expand box shadow colored to blue
        card.value.style.transform = 'scale(1.03)'
        card.value.style.boxShadow = '0 0 10px rgba(0, 0, 255, 0.1)'
        card.value.style.transition = 'all 0.5s'
    }

    const handleMouseLeave = () => {
        //transform scale to 1 and box shadow colored to black
        card.value.style.transform = 'scale(1)'
        card.value.style.boxShadow = shadow.value
        card.value.style.transition = 'all 0.5s'
    }

    onMounted(() => {
        if (card.value && cardHeader.value) {
            card.value.style.width = width.value
            card.value.style.height = height.value
            card.value.style.borderRadius = '10px'
            card.value.style.border = '1px solid #fff'
            card.value.style.boxShadow = shadow.value
            card.value.style.justifyContent = justiy.value
            cardTitle.value.style.textTransform = props.upperTitle ? 'uppercase' : 'none';
            cardSubtitle.value.style.textTransform = props.upperSubtitle ? 'uppercase' : 'none';
            cardContent.value.style.textTransform = props.upperContent ? 'uppercase' : 'none';
            cardContent.value.style.width = width.value
            cardContent.value.style.backgroundColor = backgroundColor.value
            cardContent.value.style.color = color.value
        }
    })
</script>
<template>
    <div ref="card" class="card"
        @mouseenter="handleMouseEnter"
        @mouseleave="handleMouseLeave"
    >
        <div ref="cardHeader" class="card_header">
            <h1 ref="cardTitle">{{ title }}</h1>
            <h2 ref="cardSubtitle">{{ subtitle }}</h2>
        </div>
        <div ref="cardContent" class="card_content" v-if="!htmlContent">
            <p>{{ content }}</p>
        </div>
        <div ref="cardContent" class="card_content" v-else v-html="htmlContent"></div>
    </div>
</template>
<style scoped>
    .card {
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .card_header {
        text-align: center;
    }

    .card_content {
        text-align: center;
    }

</style>
