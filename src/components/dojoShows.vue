<template>
    <div class="row">
        <div class="col-md-10 offset-md-1">
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
        <div class="col-md-12">
            <h3>Add a Show</h3>
        </div>
        <div class="col-md-10 offset-md-1">
            <div class="row">
                <div class="col-md-6">
                    <div class="form-group row">
                        <label for="inputPassword" class="col-sm-2 col-form-label">Title</label>
                        <div class="col-sm-10">
                        <input type="text" class="form-control" v-model="new_title">
                        </div>
                    </div>
                    <div class="form-group row">
                        <label for="inputPassword" class="col-sm-2 col-form-label">Genre</label>
                        <div class="col-sm-10">
                        <input type="text" class="form-control" v-model="new_genre">
                        </div>
                    </div>
                    <div class="row">
                        <div class="col-md-12">
                            <p>Is Current</p>
                            <div class="custom-control custom-radio custom-control-inline">
                                <input type="radio" id="customRadioInline1" name="customRadioInline1" class="custom-control-input" value="yes" v-model="new_current">
                                <label class="custom-control-label" for="customRadioInline1">Yes</label>
                            </div>
                            <div class="custom-control custom-radio custom-control-inline">
                                <input type="radio" id="customRadioInline2" name="customRadioInline1" class="custom-control-input" value="no" v-model="new_current">
                                <label class="custom-control-label" for="customRadioInline2">No</label>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="col-md-6">
                    <div class="form-group row">
                        <label for="inputPassword" class="col-sm-2 col-form-label">Network</label>
                        <div class="col-sm-10">
                        <input type="text" class="form-control" v-model="new_network">
                        </div>
                    </div>
                    <div class="form-group row">
                        <label for="inputPassword" class="col-sm-3 col-form-label">Number of Season</label>
                        <div class="col-sm-9">
                        <input type="number" class="form-control" v-model="new_numSeason">
                        </div>
                    </div>
                    <div class="row">
                        <div class="col-md-12">
                            <button type="button" class="btn btn-secondary btn-lg" @click="ingresar_show">Add Show</button>
                        </div>
                    </div>                    
                </div>
            </div>            
        </div>
    </div>        
</template>

<script>

import {db} from '@/firebase'

export default {
    name:'dojoShows',
    data(){
        return{
            new_title:'',
            new_network:'',
            new_numSeason:0,
            new_current:false,
            new_genre:''
        }
    },
    methods:{
        ingresar_show(){
            db.collection('shows').add({
                title:this.new_title,
                network:this.new_network,
                numberOfSeasons:parseInt(this.new_numSeason),
                isCurrent: this.new_current == 'si' ? true : false,
                genres:this.new_genre
            })
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