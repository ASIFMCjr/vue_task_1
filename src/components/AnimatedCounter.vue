<!-- <script src="https://cdn.jsdelivr.net/npm/gsap@3.12.2/dist/gsap.min.js"></script> -->
<template>
    <span id="animated-number-demo">
        <!-- <input v-model.number="number" type="number" step="20"> -->
        {{ animatedNumber }}
      </span>
  </template>
  
  <script>
  import gsap from 'gsap'
  export default {
    props: {
        number: Number
    },
  data () {
    return {
        // number: 0,
        tweenedNumber: 0
    }
    
  },
  computed: {
    animatedNumber: function() {
      return this.tweenedNumber.toFixed(0);
    }
  },
  watch: {
    number: function(newValue) {
      gsap.to(this.$data, { duration: 0.5, tweenedNumber: newValue });
    }
  }
  }
  </script>