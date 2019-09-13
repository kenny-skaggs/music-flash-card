<template>
    <div class="note-arranger">
        <img class="staff" src="../assets/staff.svg" />
        <treble-note-range-display
            v-if='showTreble'
            :octave='octave'
            :note='note'
            :noteTopStaffOffsets='noteTopStaffOffsets'
        />
        <bass-note-range-display
            v-if='!showTreble'
            :octave='octave'
            :note='note'
            :noteTopStaffOffsets='noteTopStaffOffsets'
        />
        <div v-if='showAnswer' class='note-name'>{{ note.toUpperCase() }}</div>
    </div>
</template>

<script>
import TrebleNoteRangeDisplay from "./TrebleNoteRangeDisplay.vue";
import BassNoteRangeDisplay from "./BassNoteRangeDisplay.vue";

export default {
    props: ['octave', 'note', 'showAnswer'],
    components: {TrebleNoteRangeDisplay, BassNoteRangeDisplay},
    data: function () {
        return {
            noteTopStaffOffsets: {
                stemUp: 14,
                stemDown: 94
            }
        };
    },
    computed: {
        showTreble: function () {
            return this.octave > 3;
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

    .staff {
        position: absolute;
        top: 45px;
        left: 0;
    }

    .note-name {
        position: absolute;
        top: 260px;
        left: 0px;
        font-size: 70px;
        width: 280px;
    }
</style>

