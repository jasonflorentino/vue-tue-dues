<template>
    <article :key="tueDue.id" v-for="tueDue in tueDues">
        <TueDue 
            @toggle-reminder="$emit('toggle-reminder', tueDue.id)"
            @delete-tueDue="$emit('delete-tueDue', tueDue.id)" 
            :tueDue="tueDue" 
        />
    </article>
</template>

<script>
import TueDue from './TueDue';

export default {
    name: 'TueDues',
    props: {
        tueDues: Array
    },
    components: {
        TueDue
    },
    emits: ['delete-tueDue', 'toggle-reminder'],
}
</script>