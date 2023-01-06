<template>
    <div class="modal is-active p-2">
        <div class="modal-background"></div>
        <div 
            class="modal-card"
            ref="modalCardRef"
        >
          <header class="modal-card-head">
            <p class="modal-card-title">Delete Note</p>
            <button 
                @click="closeModal"
                class="delete" aria-label="close"
            >
            </button>
          </header>
          <section class="modal-card-body">
            Are you sure you want to delete this note?
          </section>
          <footer class="modal-card-foot">
            <button 
                @click="closeModal"
                class="button"
            >
                Cancel
            </button>
            <button class="button is-danger">Delete Note</button>
          </footer>
        </div>
      </div>
</template>

<script setup>

    import { ref } from 'vue';
    import { onClickOutside } from '@vueuse/core'

    const props = defineProps({
        modelValue: {
            type: Boolean,
            default: false
        }
    })

    const emit = defineEmits(['update:modelValue'])

    const closeModal = () => {
        emit('update:modelValue', false)
    }

    const modalCardRef = ref(null)

    onClickOutside(modalCardRef, closeModal)
    

</script>