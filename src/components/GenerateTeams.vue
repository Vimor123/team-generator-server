<template>
    <div class="generate-teams-container">
        <form @submit="" class="generate-teams">
            <input type="number" v-model="noOfTeams" name="no-of-teams"/>
            <button class="btn" type="submit"> Generate Teams </button>
        </form>
    </div>
</template>

<script>
    export default {
        name: "GenerateTeams",
        data() {
            return {
                noOfTeams: 1
            }
        },
    }
</script>