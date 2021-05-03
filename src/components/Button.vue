<template>
    <button 
        @click="onClick()" 
        :style="{ background: color }"
    >
        {{ text }}
    </button>
</template>

<script>
export default {
    name: 'Button',
    props: {
        text: String,
        color: String
    },
    methods: {
        onClick() {
            console.log("click");
        }
    }
}
</script>

<style scoped>
button {
    height: 3rem;
    padding: .5rem 1rem;

    border: none;
    border-radius: .25rem;
    color: white;
    font-family: Avenir, Helvetica, Arial, sans-serif;
    font-size: .9rem;
    font-weight: bold;
}
</style>