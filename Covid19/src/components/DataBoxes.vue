<template>
    <div class="boxes">
        <!-- Box 1 -->
        <div class="box">
            <h3 class="cases">Cases</h3>
            <div class="new-cases">
                <span>New:</span>
                {{numberWithCommas(stats.NewConfirmed)}}
            </div>
            <div class="total-cases">
                <span>Total:</span>
                {{numberWithCommas(stats.TotalConfirmed)}}
            </div>
        </div>

         <!-- Box 2 -->
         <div class="box">
            <h3 class="cases">Deaths</h3>
            <div class="new-cases">
                <span>New:</span>
                {{numberWithCommas(stats.NewDeaths)}}
            </div>
            <div class="total-cases">
                <span>Total:</span>
                {{numberWithCommas(stats.TotalDeaths)}}
            </div>
        </div>
    </div>
</template>

<script>
    
    export default{
        name: 'DataBoxes',
        props: ['stats'],
        methods: {
            numberWithCommas(number){
                return number.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')
            }
        }
    }
</script>

<style>
    .boxes{
        margin-top: 30px;
        display: flex;
        justify-content: center;
        align-content: center;
        line-height: 1.7;
    }

    .boxes .box{
        margin: 0 40px;
        width: 300px;
        padding: 30px 20px;
        background: rgb(214, 214, 255);
        border-radius: 5px;
        text-align: center;
        box-shadow: 1px 1px 10px rgba(0, 0, 0, .5); 
    }

    .boxes .box h3{
        color: rgb(116, 116, 255);
    }

    .boxes .box span{
        font-weight: bolder;
    }
</style>