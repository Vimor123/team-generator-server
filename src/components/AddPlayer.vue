<template>
    <div class = "add-player-container">
        <input type="player-name" name="player-name" placeholder="Player name"/>
    </div>
    <div>
        <button @click="onClick()" class="btn" type="submit"> Add player </button>
    </div>
</template>

<script>
    export default {
        name: "AddPlayer",
        methods: {
            onClick() {
                console.log("I'm working")
            }
        }
    }
</script>