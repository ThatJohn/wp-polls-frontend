<template>
    <div class="poll-list-container">
        <h3>Poll list</h3>
        <ul class="poll-list" v-for="poll in allPolls" v-bind:key="poll.id">
            <li @click="onClick(poll.id)" class="poll-list-item">{{ poll.name }}</li>
        </ul>
    </div>
</template>

<script>
    import { mapGetters, mapActions } from "vuex";
    export default {
        name: "PollList",
        methods: {
            ...mapActions(["fetchPolls", "fetchPoll"]),
            onClick(id) {
                this.fetchPoll(id);
            },
        },
        computed: mapGetters(["allPolls"]),
        created() {
            this.fetchPolls();
        },
    };
</script>

<style scoped>
    .poll-list-container {
        background: #fff;
        flex: 4;
        border-radius: 15px;
        padding: 8px 16px;
    }

    .poll-list {
        list-style-type: none;
    }

    .poll-list-item {
        text-align: left;
    }

    .poll-list-item:hover {
        cursor: pointer;
        text-decoration: underline;
        color: #49b2fc;
    }
</style>
