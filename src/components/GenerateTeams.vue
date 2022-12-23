<template>
    <div class="generate-teams-container">
        <form @submit="onSubmit" class="generate-teams">
            <input type="number" v-model="noOfTeams" name="no-of-teams" placeholder="Number of teams"/>
            <button class="btn" type="submit"> Generate Teams </button>
        </form>
    </div>
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