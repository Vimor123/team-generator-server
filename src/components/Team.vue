<template>
    <div v-for="player in team">
        <h3> {{ player }} </h3>
    </div>
</template>

<script>
    export default {
        name: "Team",
        props: {
            team: Array
        }
    }
</script>