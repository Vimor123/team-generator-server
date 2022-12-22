<template>
    <h1> Team Generator </h1>
    <PlayerList @delete-player="deletePlayer" :players = players />
    <AddPlayer @add-player="addPlayer" />
</template>
  
<script>
    import PlayerList from './components/PlayerList.vue';
    import AddPlayer from './components/AddPlayer.vue';

    export default {
        name: "App",
        components: {
            PlayerList,
            AddPlayer
        },
        data() {
            return {
                players: []
            }
        },
        methods: {
            addPlayer(player) {
                this.players = [...this.players, player]
            },
            deletePlayer(player) {
                this.players = this.players.filter( (playerName) => playerName !== player)
                console.log(player + " removed")
            }
        },
        created() {
            this.players = ["Dean Dužnović", "Dario Sabljić", "Tonći Piplović", "Ivan Pilat", "Tin Švelec"]
        }
    }
</script>
  
<style scoped>
</style>