<template>
    <div>
        <input type="text" ref="id">
        <button @click="delete_candy">Delete Candy</button>
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
            delete_candy(){
                axios({
                    url: 'http://127.0.0.1:5000/api/candy',
                    method: 'DELETE',
                    data:{
                        id: this.$refs['id'].value,
                    }
                }).then(response =>{
                    console.log(response);
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