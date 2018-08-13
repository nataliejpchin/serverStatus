<template>
    <div class="col-xs-12 col-sm-6">
        <p v-if="!server">Please select a server</p>
        <p v-else> Server #{{ server.id }} selected, Status: {{ server.status }}</p>
        <hr>
        <button v-on:click="resetStatus">Change to normal</button>
    </div>

</template>

<script>
    import {
        bus
    } from '../../main';

    export default {
        data: function () {
            return {
                server: null
            }
        },
        methods: {
            resetStatus: function () {
                this.server.status = "Normal";
            }
        },
        created() {
            bus.$on('serverSelected', (data) => {
                // data is whatever data we pass through when we emit the event
                console.log(data.id);
                this.server = data;
            });
        }
    }
</script>

<style>
</style>