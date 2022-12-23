<template>
    <div v-for="(team, index) in teams" class="team-player-container">
        <h3> Team {{ index + 1 }} </h3>
        <Team :team = team />
    </div>
</template>

<script>
    import Team from './Team.vue';

    export default {
        name: "TeamList",
        props: {
            teams: Array
        },
        components: {
            Team
        }
    }
</script>