<template>
  <p v-if='step == 0' style="color: red;"><b-icon-emoji-angry/> {{msg}} <b-icon-emoji-angry/></p>
  <p v-else-if='step == 1' style="color: orange;"><b-icon-emoji-smile/> {{msg}} <b-icon-emoji-smile/></p>
  <p v-else-if='step == 2' style="color: yellowgreen;"><b-icon-emoji-laughing/> {{msg}} <b-icon-emoji-laughing/></p>
  <p v-else-if='step == 3' style="color: green;"><b-icon-emoji-sunglasses/> {{msg}} <b-icon-emoji-sunglasses/></p>
</template>

<script>
export default {
  name: 'sentence',
  props: {
    listData: Array
  }, 
  data() {
    return {
      msg: '',
      step: 0
    }
  },
  methods: {
    message() {
      const done = this.listData.filter(elm => elm.todo == false && elm).length
      const all = this.listData.length

      done == 0 
      && (this.msg = `It's time to start working you have ${all} tasks to do !!`) 
      && (this.step = 0);

      all / 2 > done && done != 0 
      && (this.msg = `Continue that way and you will finish soon, still have ${done}/${all} tasks`) 
      && (this.step = 1);

      all / 2 <= done
      && (this.msg = `Good !! you made half or more ${done}/${all} tasks`) 
      && (this.step = 2);

      all == done  
      && (this.msg = `Congratulation !! You finished all the ${done}/${all} tasks`) 
      && (this.step = 3);
    }
  },
  mounted(){
    this.message()
  },
  created: function() {
    this.$parent.$on('update-elm', this.message)
    this.$parent.$on('addnew', this.message);
  }
}  
</script>

<style scoped>
p{ text-align: center; }
</style>