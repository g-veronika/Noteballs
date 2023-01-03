<template>
    <div class="edit-note">
        <AddEditNote
            v-model="noteContent"
            bgColor="info-dark"
            ref="addEditNoteRef"
        >
            <template #buttons>
                <button 
                    class="button is-link has-background-info"
                    :disabled="!noteContent"
                >
                    Save note 
                </button>
            </template>
    </AddEditNote>
    </div>
</template>

<script setup>

    import { ref } from 'vue';
    import AddEditNote from '../components/Notes/AddEditNote.vue';

    const noteContent = ref('')
    const addEditNoteRef = ref()
    
</script>