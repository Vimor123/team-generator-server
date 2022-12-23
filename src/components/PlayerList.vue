<template>
    <div v-for="player in players">
        <div class="player-container"> 
            <span class="player-name"> {{ player }} </span>
            <i @click="removePlayer(player)" class="fas fa-xmark rm-btn"></i>
        </div>
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