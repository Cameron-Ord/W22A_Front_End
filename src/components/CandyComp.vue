<template>
    <div>
        <article>
            <!--displays candy retrieved from the api call-->
            <span v-for="(cand, i) in candy" :key="i">

                <h1>{{cand['name']}}</h1>

                <img v-bind:src="cand['image_url']">

                <p>{{ cand['description'] }}</p>
                
            </span>
        </article>
    </div>
</template>

<script>
import axios from 'axios';
    export default {
        
        data() {
            return {
                candy: []
            }
        },

        methods:{


            new_candy(){

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