<template>
    <div class = "add-player-container">
        <form @submit="onSubmit" class="add-player">
            <input type="text" v-model="player" name="player-name" placeholder="Player name" maxlength="40" class="name-input"/>
            <button class="add-btn" type="submit"><i class="fas fa-plus"></i></button>
        </form>
    </div>
</template>

<script>
    export default {
        name: "AddPlayer",
        data() {
            return {
                player: ''
            }
        },
        methods: {
            onSubmit(e) {
                e.preventDefault()

                if(!this.player) {
                    alert("Please type in the player name")
                    return
                }

                this.$emit('add-player', this.player)

                console.log(this.player + " added")

                this.player = ""
            }
        },
    }
</script>