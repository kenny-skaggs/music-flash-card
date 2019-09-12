<script>
import NoteRangeTemplate from "./NoteRangeTemplate.vue";

export default {
    extends: NoteRangeTemplate,
    data: function () {
        return {
            clefName: 'bass',
            pivotNote: {
                octave: 3,
                note: 'd'
            }
        };
    }
}
</script>

<style>
    .bass-clef {
        top: 61px;
        left: 30px;
    }
</style>
