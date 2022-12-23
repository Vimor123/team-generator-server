<template>
    <div class="title-container">
        <h1 class="title-text"> Team Generator </h1>
    </div>
    <div class="main-container">
        <div class="left-container">
            <div class="left-content-container">
                <h2 class="players-title"> Players </h2>
                <PlayerList @delete-player="deletePlayer" :players = players />
                <AddPlayer @add-player="addPlayer" />
            </div>
            <div class="left-content-container">
                <h2 class="generate-teams-title"> Generate Teams </h2>
                <GenerateTeams @generate-teams="generateTeams" />
            </div>
        </div>
        <div class="right-container">
            <TeamList :teams = teams />
        </div>
    </div>

</template>
  
<script>
    import PlayerList from './components/PlayerList.vue';
    import AddPlayer from './components/AddPlayer.vue';
    import GenerateTeams from './components/GenerateTeams.vue';
    import TeamList from './components/TeamList.vue';

    export default {
        name: "App",
        components: {
            PlayerList,
            AddPlayer,
            GenerateTeams,
            TeamList
        },
        data() {
            return {
                players: [],
                teams: []
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
                //this.players = this.players.filter( (playerName) => playerName !== player)
                let index = this.players.indexOf(player)
                this.players.splice(index, 1)
                console.log(player + " removed")
                this.persist()
            },
            persist() {
                const parsed = JSON.stringify(this.players)
                localStorage.setItem("players", parsed)
            },
            generateTeams(noOfTeams) {

                this.teams = []

                if (noOfTeams > this.players.length) {
                    alert(`There is not enough players to generate ${noOfTeams} teams`)
                    return
                }
                
                console.log(`Generating ${noOfTeams} teams`)

                for (let i = 0; i < noOfTeams; i++) {
                    this.teams.push([])
                }

                let playersCopy = [...this.players]
                let teamIndex = 0

                while(playersCopy.length > 0) {
                    let randomIndex = Math.floor(Math.random() * playersCopy.length)
                    let chosenPlayer = playersCopy[randomIndex]

                    this.teams[teamIndex].push(chosenPlayer)
                    teamIndex++
                    if(teamIndex >= noOfTeams) {
                        teamIndex = 0
                    }

                    playersCopy.splice(randomIndex, 1)
                }

                console.log(this.teams)
            }
        }
    }
</script>