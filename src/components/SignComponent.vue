<template>
    <div class="signComponent">
        <select v-model="signValue" class="signDiv">
            <option>+</option>
            <option>-</option>
            <option>*</option>
            <option>/</option>
          </select>
    </div>
</template>
<script>
export default {
    name: 'SignComponent',
    data () {
        return {
            signValue: "+"
        }
    },
    watch: {
        signValue: function(newSignValue) {
            this.$emit("signValue", newSignValue)
        }
    }
}
</script>
<style>
    .signComponent {
        margin-right: 10px;
    }
    .signDiv {}
    
</style>