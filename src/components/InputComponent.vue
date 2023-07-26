<template>
    <div class="inputComponent">
        <input class="inputDiv"
        v-model.number = "inputValue" 
        step="10"
        type="number" 
        placeholder="0" />
        <!-- {{ animatedInputValue }}    -->
    </div>
</template>
<script src="https://cdn.jsdelivr.net/npm/tween.js@16.3.4"></script>
<script>
export default {
    name: 'InputComponent',
    data () {
        return {
            inputValue: 0,
            animatedInputValue: 0
        }
    },
    methods: {
        changeValue(event) {
            this.inputValue = event.target.value
        }
    },
    watch: {
        inputValue: function(newInputValue) {
            this.$emit("inputValue", newInputValue)
            
        }
    },
    computed: {
        inputValue() {
      return this.text || 0
    }
  }
}
</script>
<style>
    .inputComponent {
        margin-right: 10px;
    }
    .inputDiv {
        width: 50px;
        
    }
</style>