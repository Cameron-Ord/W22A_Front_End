<template>
    <div>
        <candy-comp></candy-comp>
        <add-candy></add-candy>
 
    </div>
</template>

<script>
import CandyComp from '@/components/CandyComp.vue';
import AddCandy from '@/components/AddCandy.vue';

    export default {

        components:{
            CandyComp,
            AddCandy,

        }
        
    }
</script>

<style lang="scss" scoped>

</style>