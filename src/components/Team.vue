<template>
    <div v-for="player in team" class="player-in-team-container">
        <span class="player-in-team-name"> {{ player }} </span>
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