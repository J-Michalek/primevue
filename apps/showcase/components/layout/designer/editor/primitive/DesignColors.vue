<template>
    <Fieldset legend="Colors" :toggleable="true">
        <template v-for="(value, key) of $appState.designer.theme.preset.primitive" :key="key">
            <section v-if="key !== 'borderRadius'" class="flex justify-between items-center mb-4 gap-8">
                <div class="flex gap-2 items-center">
                    <span class="text-sm capitalize block w-20">{{ key }}</span>
                    <input :value="$appState.designer.theme.preset.primitive[key]['500']" @input="onColorChange($event, key)" type="color" />
                </div>
                <DesignColorPalette :value="$appState.designer.theme.preset.primitive[key]" />
            </section>
        </template>
    </Fieldset>
</template>

<script>
import { palette } from '@primevue/themes';

export default {
    methods: {
        onColorChange(event, color) {
            this.$appState.designer.theme.preset.primitive[color] = palette(event.target.value);
        }
    }
};
</script>

<style scoped>
[type='color'] {
    border: 0 none;
    padding: 0;
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    width: 28px;
    height: 28px;
    background-color: transparent;
    border: none;
    cursor: pointer;
}

[type='color']::-webkit-color-swatch {
    border-radius: 4px;
    width: 24px;
    height: 24px;
    border: 0 none;
}
</style>
