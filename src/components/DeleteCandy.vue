<template>
    <div>
        <!--input prompts-->
        <input type="text" ref="id">
        <button @click="delete_candy">Delete Candy</button>
        <!--displays api status when it's defined by the api call-->
        <p v-if="status !== undefined">Rows Deleted: {{ status }}</p>
    </div>
</template>

<script>
import axios from 'axios';

    export default {
        
        data() {
            return {
                status: undefined
            }
        },

        methods: {

            //api delete function//

            delete_candy(){
                axios({
                    url: 'http://127.0.0.1:5000/api/candy',
                    method: 'DELETE',
                    data:{
                        //getting value from input tag//
                        id: this.$refs['id'].value,
                    }
                }).then(response =>{
                    console.log(response);
                    //on api success, displays the amount of rows deleted in a status message//
                    this.status = response['data'][0]['row_count()'];
                }).catch(error =>{
                    error;
                    this.status = "Something went wrong."
                })
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>