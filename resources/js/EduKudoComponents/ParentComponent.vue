<script setup>
import { ref } from 'vue';
import ChildComponent from './ChildComponent.vue';

const parentState = ref({
    isBoolean: true,
    textValue: 'Initial Test Value',
});

const toggleBoolean = () => {
    parentState.value.isBoolean = !parentState.value.isBoolean;
};

const updateText = (newText) => {
    parentState.value.textValue = newText;
};
</script>

<template>
    <div class="p-4 border rounded bg-gray-100">
        <h3 class="text-md font-semibold mb-2">Parent Component path: (resources/js/EduKudoComponents/ParentComponent.vue)</h3>
        <p class="mb-2"><span class="font-bold">Boolean Value: </span> {{ parentState.isBoolean }}</p>
        <p class="mb-4"> <span class="font-bold">String Value: </span> {{ parentState.textValue }}</p>

        <ChildComponent
            :boolean-value="parentState.isBoolean"
            :text-value="parentState.textValue"
            @toggle-boolean="toggleBoolean"
            @update-text="updateText"
        />
    </div>
</template>
