<template>
    <div class="edit-note">
        <AddEditNote
            v-model="noteContent"
            ref="addEditNoteRef"
        >
            <template #buttons>
                <button 
                    class="button is-link has-background-success"
                >
                    Add New Note 
                </button>
            </template>
    </AddEditNote>
    </div>
</template>

<script setup>

    import { ref } from 'vue';
    import AddEditNote from '../components/Notes/AddEditNote.vue';

    const noteContent = ref('test')
    const addEditNoteRef = ref()
    
</script>