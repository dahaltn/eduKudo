<script setup>
import { defineProps, defineEmits } from 'vue';

defineProps({
    booleanValue: {
        type: Boolean,
        required: true,
    },
    textValue: {
        type: String,
        required: true,
    },
});

const emit = defineEmits(["toggle-boolean", "update-text"]);

const handleToggle = () => {
    emit("toggle-boolean");
};

const handleTextChange = (event) => {
    emit("update-text", event.target.value);
};
</script>

<template>
    <div class="p-4 border rounded bg-gray-200">
        <h4 class="text-sm font-medium mb-2">Child Component Path: (resources/js/EduKudoComponents/ChildComponent.vue)</h4>
        <button class="px-3 py-1 mb-3 bg-blue-500 text-white rounded" @click="handleToggle">
            Toggle Boolean
        </button>
        <input
            type="text"
            class="border p-2 rounded w-full"
            :value="textValue"
            @input="handleTextChange"
        />
    </div>
</template>
