<template>
    <header>
        <h1>{{ title }}</h1>
        <Button text="Add Tue-Due" color="#3eaf7c" />
    </header>
</template>

<script>
import Button from './Button';

export default {
    name: 'Header',
    props: {
        title: String
    },
    components: {
        Button
    }
}
</script>

<style scoped>
    header {
        padding: 1rem;
        display: flex;
        justify-content: space-between;
    }
</style>