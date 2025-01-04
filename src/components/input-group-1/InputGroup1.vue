<template>
   
    <div class="input-group mb-3">
        <input @keypress="onKeyPress" v-model="value" type="text" class="form-control p-2" placeholder="Task item" aria-label="Task item" aria-describedby="button-addon2">
        <button @click="emitValue" class="btn btn-primary" type="button" id="button-addon2">Button</button>
    </div>

</template>

<script>
export default {
    props:{
        
    },
    data(){
        return{
            value: ''
        }
        
    },
    methods:{
        emitValue(){
            this.$emit('data-item', this.value)
            this.value = ''
        },
        onKeyPress(event){
            if(event.key == "Enter")
                this.emitValue()
        }
    }
}
</script>