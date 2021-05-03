<template>
    <div 
        @dblclick="$emit('toggle-reminder', tueDue.id)"
        :class="[tueDue.reminder ? 'reminder' : '', 'tueDue']"
    >
        <div>
            <h3>{{ tueDue.text }}</h3>
            <p>{{ tueDue.day }}</p>
        </div>
        <div>
            <i 
                @click="$emit('delete-tueDue', tueDue.id)" 
                class="far fa-times-circle"
            ></i>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TueDue',
    props: {
        tueDue: Object
    },
}
</script>

<style scoped>

.far {
    font-size: 1.2rem;
    padding: .3rem;
    opacity: .7;
    color: #0a643b;
}
.far:hover {
    opacity: 1;
    cursor: pointer;
}

.tueDue {
    margin: 1rem;
    padding: 1rem;
    display: flex;
    justify-content: space-between;

    border: 1px solid #3eaf7c;
    border-radius: .25rem;
    background-color:#c1ebd9;
}

.reminder {
    border-left-width: 6px;
}

</style>