<script>
import NoteRangeTemplate from "./NoteRangeTemplate.vue";

export default {
    extends: NoteRangeTemplate,
    data: function () {
        return {
            clefName: 'treble',
            pivotNote: {
                octave: 4,
                note: 'b'
            }
        };
    },
    computed: {
        noteGraphic: function () {
            if (this.note == 'c' && this.octave == 4) {
                return 'treble-middle-c';
            } else {
                if (this.stemUp) {
                    return "note-stem-up";
                } else {
                    return "note-stem-down";
                }
            }
        }
    }
}
</script>

<style>
    .treble-clef {
        top: 2px;
        left: 20px;
    }
</style>
