<template>
    <li v-for="(item, index) in items" :key="index">
        <div class="item-box">
            <div class="form-check">
                <input class="form-check-input" type="checkbox" value="" :id="'flexCheckChecked-'+index" v-model="item.checked" >
                <label class="form-check-label" :for="'flexCheckChecked-'+index">
                    <a :class="{active: item.checked}" href="#">{{ item.text }}</a>
                </label>
            </div>
            <a href="#" @click="emitKey(index)"><i class="bi bi-x-lg"></i></a>

        </div>

        

    </li>
</template>

<script>
export default{
    props:{
        items: {
            type: Array,
            require: true
        }
    },
    methods:{
        emitKey(index){
            this.$emit('delete-task',index)
        }
    }
}
</script>

<style>
li{
    list-style: none;
    margin: 0;
    padding: 0;
    text-align: left;
}
.item-box{
    display: flex;
    justify-content: space-between;
}
label a{
    color: black;
    text-decoration: none;
}
label a.active{
    text-decoration: line-through;
}
</style>