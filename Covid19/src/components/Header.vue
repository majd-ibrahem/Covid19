<template>
    <header>
        <div><i class="fas fa-viruses"></i> Covid-19 Tracker</div>
        <p>API by 
        <a href="https://covid19api.com" target="_blank">covid19api</a>
        </p>
    </header>
</template>

<script>
    export default{
        name: 'Header',
    }
</script>

<style scoped>
     header{
        text-align: center;
        background: linear-gradient(to left, rgb(72, 72, 255), rgb(125, 125, 255));
        color: white;
        padding: 5px;
        font-size: 1.5rem;
     }

    header p{
        margin-top: 5px;
     }

    header a{
        color: rgb(175, 175, 253);
        text-decoration: none;
     }
    header i{
        font-size: 1.9rem;
     }
</style>