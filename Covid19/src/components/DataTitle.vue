<template>
    <div class="date">
        <h2>{{text}}</h2>
        <p>{{timestamp()}}</p>
    </div>
</template>

<script>
import moment from 'moment'
    export default{
        name: 'DataTitle',
        props: ['text', 'dataDate'],
        methods: {
            timestamp(){
               return moment(this.dataDate).format('MMMM Do YYYY, h:mm:ss a')
            },
        }
    }
</script>

<style>
    .date{
        margin-top: 50px;
        text-align: center;
    }
</style>