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
        mounted() {
            if(localStorage.getItem("players")) {
                try {
                    this.players = JSON.parse(localStorage.getItem("players"))
                } catch(e) {
                    localStorage.removeItem("players")
                }
            }
        },
        methods: {
            addPlayer(player) {
                this.players = [...this.players, player]
                this.persist()
            },
            deletePlayer(player) {
                this.players = this.players.filter( (playerName) => playerName !== player)
                console.log(player + " removed")
                this.persist()
            },
            persist() {
                const parsed = JSON.stringify(this.players)
                localStorage.setItem("players", parsed)
            }
        }
    }
</script>
  
<style scoped>
</style>