<template>
    <li class="list-group-item" style="cursor: pointer" v-on:click="serverSelected">
        Server #{{ server.id }}
    </li>
</template>

<script>
    import {
        bus
    }
    from '../../main'
    export default {
        props: ['server'],
        methods: {
            serverSelected: function () {
                bus.$emit('serverSelected', this.server);
            }
        }
    }
</script>

<!-- Loop through all the components, pass the id and status to that, be able to click and then load the server in server details-->

<style>
</style>