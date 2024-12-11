<script setup>
import {ref, watch} from 'vue';
import less from 'less';

const htmlCode = ref(`<div class="preview">
                        Welcome to EduKUDO dev challenge.
                        <p class="child">Child Text here.</p>
                        </div>`);

const lessCode = ref(`
    @default-bg: skyblue;
    @default-color: white;
    @default-font-weight: bold;

    .preview {
        display: block;
        width:100%;
        background: @default-bg;
        color: @default-color;
        font-weight: @default-font-weight;
        padding: 20px;
        border-radius: 8px;
        text-align: center;
    }

    .child {
        background: lighten(@default-bg, 20%);
        color: @default-color;
        padding: 10px;
        border-radius: 5px;
        margin-top: 10px;
        display: inline-block;
    }
`);

const compiledCss = ref('');

const compileLess = async () => {
    try {
        const output = await less.render(lessCode.value);
        compiledCss.value = output.css;
    } catch (error) {
        compiledCss.value = `/* Error: ${error.message} */`;
    }
};

watch(lessCode, compileLess, {immediate: true});
</script>

<template>
    <div class="p-4 border rounded bg-gray-100">
        <h3 class="text-md font-semibold mb-4">LESS and HTML Editor</h3>
        <div class="flex gap-4">
            <div class="w-1/2">
                <label for="html-editor" class="block mb-2 font-medium">HTML Code</label>
                <textarea
                    id="html-editor"
                    v-model="htmlCode"
                    class="w-full p-2 border rounded h-72 resize-none"
                ></textarea>
            </div>
            <div class="w-1/2">
                <label for="less-editor" class="block mb-2 font-medium">LESS Code</label>
                <textarea
                    id="less-editor"
                    v-model="lessCode"
                    class="w-full p-2 border rounded h-72"
                ></textarea>
            </div>
        </div>
        <div class="mt-6 p-4 border rounded bg-white">
            <h4 class="font-medium mb-2">Preview</h4>
            <div style="border: 1px solid #ddd; padding: 16px;" v-html="htmlCode" :style="compiledCss"></div>
        </div>
    </div>
</template>
