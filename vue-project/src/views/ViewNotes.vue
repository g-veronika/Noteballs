<template>
    <div class="notes">

        <AddEditNote
            ref="AddEditNoteRef"
            @update:modelValue="newNote = $event"
            v-model="newNote">
        >
            <template #buttons>
                <button 
                @click="addNote"
                :disabled="!newNote"
                class="button is-link has-background-success"
            >
                Add New Note 
                </button>
            </template>
        </AddEditNote>

        <Note
            v-for="note in storeNotes.notes"
            :key="note.id"
            :note="note"
        />
    </div>
</template>

<script setup>

    import { ref } from 'vue';
    import Note from '@/components/Notes/Note.vue'
    import AddEditNote from '@/components/Notes/AddEditNote.vue'
    import { useStoreNotes } from '@/stores/storeNotes'

    const storeNotes = useStoreNotes()    

    const newNote = ref('')
    const AddEditNoteRef = ref(null)

    const addNote = () => {
        storeNotes.addNote(newNote.value)
        newNote.value = ''
        AddEditNoteRef.value.focusTextarea()
    }

</script>