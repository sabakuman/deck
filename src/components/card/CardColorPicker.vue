<template>
    <div class="color-picker">
        <div class="color-options">
            <div v-for="color in availableColors" 
                 :key="color.value"
                 :class="['color-option', { 'selected': modelValue === color.value }]"
                 :style="{ backgroundColor: color.value }"
                 @click="$emit('update:modelValue', color.value)">
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'CardColorPicker',
    props: {
        modelValue: {
            type: String,
            default: null
        }
    },
    data() {
        return {
            availableColors: [
                { name: 'Default', value: null },
                { name: 'Red', value: '#ffcdd2' },
                { name: 'Green', value: '#dcedc8' },
                { name: 'Blue', value: '#bbdefb' },
                { name: 'Yellow', value: '#fff9c4' },
                { name: 'Purple', value: '#e1bee7' },
                { name: 'Orange', value: '#ffe0b2' },
                { name: 'Grey', value: '#e0e0e0' }
            ]
        }
    }
}
</script>

<style lang="scss" scoped>
.color-picker {
    padding: 8px;
    border-radius: var(--border-radius);
    background-color: var(--color-main-background);

    .color-options {
        display: flex;
        flex-wrap: wrap;
        gap: 8px;
        justify-content: center;
    }

    .color-option {
        width: 24px;
        height: 24px;
        border-radius: 50%;
        border: 2px solid var(--color-border);
        cursor: pointer;
        transition: transform 0.1s ease;

        &:hover {
            transform: scale(1.1);
        }

        &.selected {
            border-color: var(--color-primary);
        }
    }
}
</style>