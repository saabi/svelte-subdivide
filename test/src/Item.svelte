<script context='module'>
</script>
<script>
    import { getIndex } from './counter.js';

    let index = getIndex();
    export let message = '';

</script>

<span>{index}{message== '' ? '' : ' - ' + message}</span>
