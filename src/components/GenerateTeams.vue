<template>
    <form @submit="onSubmit" class="generate-teams">
        <div class="no-of-teams-row">
            <span class="no-of-teams-text"> Number of teams: </span>
            <input type="number" v-model="noOfTeams" name="no-of-teams" class="no-of-teams-input"/>
        </div>
        <button class="generate-teams-btn" type="submit"> Generate </button>
    </form>
</template>

<script>
    export default {
        name: "GenerateTeams",
        data() {
            return {
                noOfTeams: ''
            }
        },
        methods: {
            onSubmit(e) {
                e.preventDefault()

                if (!this.noOfTeams) {
                    alert("Please type in the number of teams")
                    return
                }

                this.$emit('generate-teams', this.noOfTeams)
            }
        },
        emits: ['generate-teams']
    }
</script>