<template>
    <div 
        class="card p-4 mb-5"
        :class="`has-background-${ bgColor }`"
    >

        <label
            v-if="label" 
            class="has-text-white mb-6">
                {{ label }}
        </label>

        <div class="field">
            <div class="control ">
                <textarea 
                    :value="modelValue" 
                    class="textarea" 
                    :placeholder="placeholder" 
                    ref="textareaRef"
                    @input="(event) => $emit('update:modelValue', event.target.value)"
                    v-autofocus
                />
            </div>
        </div>
          
        <div class="field is-grouped is-grouped-right">
            <div class="control">
                <slot name="buttons" />
            </div>
        </div>
    </div>
</template>

<script setup>

    import { ref } from 'vue';
    import { vAutofocus } from '@/directives/vAutofocus'
    
    const props = defineProps({
        modelValue: {
            type: String,
            required: true
        },
        bgColor: {
            type: String,
            default: 'success-dark'
        },
        placeholder: {
            type: String,
            default: 'Type something'
        },
        label: {
            type: String,
        }
    })

    const textareaRef = ref(null)

    const focusTextarea = () => {
        textareaRef.value.focus()
    }

    defineExpose({
        focusTextarea
    })

</script>