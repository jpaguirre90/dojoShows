<template>
    <div class="row">
        <div class="col-md-12">
            <table class="table table-dark">
                <thead>
                    <tr>
                        <th scope="col">#</th>
                        <th scope="col">Title</th>
                        <th scope="col">Network</th>
                        <th scope="col">Number of Season</th>
                        <th scope="col">Is Current</th>
                        <th scope="col">Genres</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(show, i) in shows" :key="show.id">    
                        <th scope="row">{{i+1}}</th>   
                        <td>{{ show.title }} </td>
                        <td>{{ show.network }}</td>
                        <td>{{ show.numberOfSeasons }}</td>
                        <td>{{ show.isCurrent }}</td>
                        <td>{{ show.genres }}</td>
                    </tr>
                </tbody>
            </table>             
        </div>
    </div>        
</template>

<script>

import {db} from '@/firebase'

export default {
    name:'dojoShows',
    data(){
        return{
            suma:0,
        }
    },
    firestore(){
        return{
        shows: db.collection('shows')
        }
    }
}

</script>

<style>

</style>