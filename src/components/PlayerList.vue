<template>
    <div v-for="player in players">
        <h3> {{ player }} <i @click="removePlayer(player)" class="fas fa-trash rm-btn"></i></h3>
    </div>
</template>

<script>
    export default {
        name: "PlayerList",
        props: {
            players: Array
        },
        methods: {
            removePlayer(player) {
                this.$emit('delete-player', player)
            }
        },
        emits: ['delete-player']
    }
</script>

<style scoped>
    .rm-btn {
        color: rgb(6, 87, 60)
    }
</style>