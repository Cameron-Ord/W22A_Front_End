<template>
    <div>
        <article>
            <span>
                <input type="text" ref="name_input">
                <input type="text" ref="image_input">
                <input type="text" ref="description_input">
                <button @click="create_candy">Add Candy</button>
                <p>{{ status }}</p>
            </span>
        </article>
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

    methods:{

        create_candy(){

            axios({

                url:'http://127.0.0.1:5000/api/candy',
                method: 'POST',
                data:{
                    name: this.$refs['name_input'].value,
                    image_url: this.$refs['image_input'].value,
                    description: this.$refs['description_input'].value,
                }
            }).then(response =>{
                response;
                this.status = "New candy inserted";
            }).catch(error =>{
                error;
                this.status = "Sorry, something went wrong";
            })
        }

    },

    mounted(){

    }
}
</script>

<style lang="scss" scoped>

</style>