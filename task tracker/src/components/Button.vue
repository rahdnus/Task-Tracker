<template >
    <div class="center">
        <button @click="onClick" class="btn" :style="{background:color}" >{{ text }}</button>
    </div>
</template>

<script>
export default {
    name: "Button",
    components: {},
    props:{
        text:String,
        color:String
    },
    methods:{
        onClick()
        {
            this.$emit('toggleshow');
        }
    }
}
</script>

<style>
.center{
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
