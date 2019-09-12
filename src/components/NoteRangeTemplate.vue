<template>
    <div class="note-arranger">
        <img :class='"clef " + clefName + "-clef"'
        :src='"../assets/" + clefName + "-clef.svg"' />
        <img
            class="note"
            :src='"../assets/" + noteGraphic + ".svg"'
            :style='{ top: noteTop }'
        />
    </div>
</template>

<script>
export default {
    props: ['octave', 'note', 'noteTopStaffOffsets'],
    data: function () {
        return {
            distanceBetweenNotes: 15
        };
    },
    computed: {
        noteTop: function () {
            let topOffset = this.stemUp ?
                this.noteTopStaffOffsets.stemUp :
                this.noteTopStaffOffsets.stemDown;

            return (this.currentNotePosition - this.baseNotePosition) * this.distanceBetweenNotes
                + topOffset + "px";
        },
        currentNotePosition: function () {
            return this.notePosition(this.octave, this.note);
        },
        baseNotePosition: function () {
            return this.notePosition(this.pivotNote.octave, this.pivotNote.note)
        },
        stemUp: function () {
            return this.currentNotePosition > this.baseNotePosition;
        },
        noteGraphic: function () {
            if (this.stemUp) {
                return "note-stem-up";
            } else {
                return "note-stem-down";
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
    .clef, .note {
        position: absolute;
    }

    .note {
        left: 170px;
    }
</style>
