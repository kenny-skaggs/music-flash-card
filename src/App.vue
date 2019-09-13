<template>
  <div id="app" @click='userClicked'>
    <NoteArranger
        :octave=currentNote.octave
        :note=currentNote.note
        :showAnswer=!isUserGuessing
    />
    <footer>
        <a href="https://www.freepik.com/free-photos-vectors/music" target="_blank">
            Music vectors created by rawpixel.com - www.freepik.com
        </a>
    </footer>
  </div>
</template>

<script>
import NoteArranger from './components/NoteArranger.vue'

export default {
    name: 'app',
    components: {
        NoteArranger
    },
    data: function () {
        return {
            currentNote: {},
            noteIndex: 0,
            notes: this.buildNotes(),
            isUserGuessing: true
        };
    },
    created: function () {
        this.nextNote();
    },
    methods: {
        userClicked: function () {
            if (this.isUserGuessing) {
                this.isUserGuessing = false;
            } else {
                this.nextNote();
                this.isUserGuessing = true;
            }
        },
        nextNote: function () {
            this.currentNote = this.notes[this.randomNoteIndex()];
        },
        randomNoteIndex: function () {
            return Math.floor(Math.random() * this.notes.length);
        },
        buildNotes: function () {
            let notes = [],
                octave = 2,
                note = 'f';

            while (octave != 5 || note != 'a') {  // Stop at note g5
                notes.push({
                    octave: octave,
                    note: note
                });

                note = String.fromCharCode(note.charCodeAt(0) + 1);
                if (note == 'h') {
                    note = 'a';
                } else if (note == 'c') {
                    octave += 1;
                }
            }

            return notes;
        }
    }
}
</script>

<style>
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        height: 80vh;

        user-select: none;  /* Disabling highlighting indicator for when the user clicks fast (double clicks) */
    }

    footer {
        width: 100%;
        position: fixed;
        bottom: 10px;
    }
</style>
