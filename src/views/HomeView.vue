<template>
    <div>
        <candy-comp></candy-comp>
        <add-candy></add-candy>
        <delete-candy></delete-candy>
    </div>
</template>

<script>
import CandyComp from '@/components/CandyComp.vue';
import AddCandy from '@/components/AddCandy.vue';
import DeleteCandy from '@/components/DeleteCandy.vue';
    export default {

        components:{
            CandyComp,
            AddCandy,
            DeleteCandy
        }
        
    }
</script>

<style lang="scss" scoped>

</style>