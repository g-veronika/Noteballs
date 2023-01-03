<template>
    <div class="card has-background-success-dark p-4 mb-5">
        <div class="field">
            <div class="control">
                <textarea 
                    :value="modelValue" 
                    class="textarea" 
                    placeholder="Add a new note" 
                    ref="textareaRef"
                    @input="(event) => $emit('update:modelValue', event.target.value)"
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

    
    const props = defineProps({
        modelValue: {
            type: String,
            required: true
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