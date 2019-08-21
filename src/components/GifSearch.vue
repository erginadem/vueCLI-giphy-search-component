<template>
    <div class="container">
        <div class="">
            <div class="mt-3">
                <form  @submit.prevent="doSearch">
                    <input v-model="query" type="text" placeholder="GIF search" class="form-control" />
                    <button type="submit" class="btn btn-primary mt-3">Go</button>
                </form>
            </div>
            <div class="list-group">
                <img :image="result.image.fixed.height.url" v-for="result in results" />
            </div>
        </div>
    </div>
</template>



<script>
import axios from 'axios'

export default {

    data() {
        return {
            appKey: 'Nm40IfiNHYRUHKH6xPkuljyfoFLnUfC9',
            showDropdown: false,
            showResults: false,
            query: '',
            results: [ ],
        }
    },

    methods: {


        doSearch() {
            axios.get('https://api.giphy.com/v1/gifs/search?api_key=' + this.appKey + '&q=' +this.query)
                .then( (response) => {
                    console.log(response.data.data)
                })
        },
    },
}
</script>



<style lang="css" scoped>
</style>
