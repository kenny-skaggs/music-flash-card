<template>
    <div class="note-arranger">
        <img class="staff" src="../assets/staff.svg" />
        <img class="treble-clef" src="../assets/treble-clef.svg" />
        <img class="bass-clef" src="../assets/bass-clef.svg" />
        <img
            class="note"
            src="../assets/note-stem-up.svg"
            :style='{ top: noteTop }'
        />
    </div>
</template>

<script>
export default {
    props: ['octave', 'note'],  // 15px between each note
    data: function () {
        return {
            pivotNote: {
                octave: 4,
                note: 'b',
                topOffset: 14
            }
        };
    },
    computed: {
        noteTop: function () {
            return (this.currentNotePosition - this.baseNotePosition) * 15 + this.pivotNote.topOffset + "px";
        },
        currentNotePosition: function () {
            return this.notePosition(this.octave, this.note);
        },
        baseNotePosition: function () {
            return this.notePosition(this.pivotNote.octave, this.pivotNote.note)
        },
        stemUp: function () {
            if (this.octave < 4) {
                return true;
            } else if (this.octave == 4 && this.note < 'b') {
                return true;
            } else {
                return false;
            }
        }
    },
    methods: {
        notePosition: function(octave, note) {
            return -(octave * 7 + ['c', 'd', 'e', 'f', 'g', 'a', 'b'].indexOf(note));
        }
    }
}
</script>

<style>
    .note-arranger {
        position: relative;
        width: 200px;
        margin: auto;
    }

    .treble-clef, .bass-clef, .staff, .note {
        position: absolute;
    }

    .staff {
        top: 45px;
        left: 0;
    }

    .treble-clef {
        top: 2px;
        left: 20px;
    }

    .bass-clef {
        top: 61px;
        left: 30px;
    }

    .note {
        left: 160px;
    }
</style>

