<template>
    <div>
        <article>
            <!--displays candy retrieved from the api call-->
            <span v-for="(cand, i) in candy" :key="i">

                <h1>{{cand['name']}}</h1>

                <img v-bind:src="cand['image_url']">

                <p>{{ cand['description'] }}</p>
                
                <button @click="delete_candy" ref="candy_clicked" :clicked="i">Delete Candy</button>
                <p v-if="status !== undefined">Rows Deleted: {{ status }}</p>
            </span>
        </article>
    </div>
</template>

<script>
import axios from 'axios';
    export default {
        
        data() {
            return {
                candy: [],
                status: undefined
            }
        },

        methods:{


            delete_candy(details){

                this.$refs['candy_clicked'] = details.currentTarget;
                let button_clicked = this.$refs['candy_clicked'].getAttribute('clicked');
                let candy_clicked = this.candy[button_clicked]['id'];


                axios({
                    url: 'http://127.0.0.1:5000/api/candy',
                    method: 'DELETE',
                    data:{
                        //getting value from input tag//
                        id: candy_clicked,
                    }
                    }).then(response =>{
                        console.log(response);
                        //on api success, displays the amount of rows deleted in a status message//
                        this.status = response['data'][0]['row_count()'];
                    }).catch(error =>{
                        error;
                        this.status = "Something went wrong."
                        })
                        },

            get_candy(){

                //api get call for the candy//

                axios({
                    method: 'GET',
                    url:'http://127.0.0.1:5000/api/candy'
                }).then(response =>{

                    //loops through data and pushes it into to the candy array//

                    for(let i=0; i < response['data'].length; i++){
                        this.candy.push(response['data'][i]);
                    }


                }).catch(error =>{

                    error;
                    
                })

            }

        },


        mounted(){

            //on page mount, calls the api function//
            this.get_candy();

        }
    }
</script>

<style lang="scss" scoped>

img{
    width: 25%;
}

</style>