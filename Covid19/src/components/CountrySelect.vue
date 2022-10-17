<template>
    <select v-model="selected" @change="onChange">
        <option value="0">Select Country</option>
        <option v-for="country in countries" :value="country.ID">
            {{country.Country}}
        </option>
    </select>
</template>

<script>
    export default{
        name: 'CountrySelect',
        props: ['countries'],
        data(){
            return{
                selected: 0
            }
        },
        methods: {
            onChange(){
                const country = this.countries.find((item) => item.ID === this.selected)
                this.$emit('getCountry', country)
            }
        }
    }


</script>

<style>
    select{
        display: block;
        margin: 0 auto;
        margin-top: 30px;
        width: 685px;
        outline: 0;
        padding: 10px;
        font-size: 1.1rem;
    }
</style>