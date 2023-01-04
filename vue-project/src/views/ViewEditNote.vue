<template>
    <div class="edit-note">
        <AddEditNote
            v-model="noteContent"
            bgColor="info-dark"
            ref="addEditNoteRef"
            placeholder="Edit note"
            label="Edit Note"
        >
            <template #buttons>
                <button
                    @click="$router.back()" 
                    class="button is-link is-light"
                >
                    Cancel
                </button>
                <button 
                    @click="handleSaveClicked"
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
    import { useRoute } from 'vue-router'
    import AddEditNote from '../components/Notes/AddEditNote.vue';
    import { useStoreNotes } from '@/stores/storeNotes'

    const storeNotes = useStoreNotes()

    const route = useRoute()
 
    const noteContent = ref('')
    // const addEditNoteRef = ref()

    noteContent.value = storeNotes.getNoteContent(route.params.id)

    const handleSaveClicked = () => {
        storeNotes.updateNote(route.params.id, noteContent.value)
    }

</script>