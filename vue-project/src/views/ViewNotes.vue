<template>
    <div class="notes">

        <div class="card has-background-success-dark p-4 mb-5">
            <div class="field">
                <div class="control">
                    <textarea 
                        v-model="newNote"
                        class="textarea" 
                        placeholder="Add a new note" 
                        ref="newNoteRef"
                    />
                </div>
            </div>
              
            <div class="field is-grouped is-grouped-right">
                <div class="control">
                    <button 
                        @click="addNote"
                        :disabled="!newNote"
                        class="button is-link has-background-success"
                    >
                        Add New Note
                    </button>
                </div>
            </div>
        </div>

        <div 
            v-for="note in notes"
            :key="note.id"
            class="card mb-4"
        >
            <div class="card-content">
                <div class="content">
                    {{ note.content }}
                </div>
            </div>
            <footer class="card-footer">
                <a href="#" class="card-footer-item">Edit</a>
                <a href="#" class="card-footer-item">Delete</a>
            </footer>
        </div>
    </div>
</template>

<script setup>

    import { ref } from 'vue';

    const newNote = ref('')

    const newNoteRef = ref(null)


    const notes = ref([
        {
            id: 'id1',
            content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Earum atque quas facilis sed, provident a animi doloribus consectetur qui fuga laudantium, ipsam aliquid corporis quos! Nulla maiores animi quasi cum.'
        },
        {
            id: 'id2',
            content: 'This is a shorter note !'
        }
    ])

    const addNote = () => {

        let currentDate = new Date().getTime(),
            id = currentDate.toString()

        let note = {
            id,
            content: newNote.value
        }

        notes.value.unshift(note)
        newNote.value = ''

        newNoteRef.value.focus()
    }

</script>