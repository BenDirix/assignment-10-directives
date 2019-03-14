<template>
  <div class="container">
    <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <h1>Directives Exercise</h1>
        <!-- Exercise -->
        <!-- Build a Custom Directive which works like v-on (Listen for Events) -->
        <p v-customOn:click="isAFunction">click me</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    data(){
    return{
      notAFunction: 'Not a function'
    }
  },

  methods: {
    isAFunction() {
      return "This text was changed by my custom v-on directive";
    }
  },
  directives:{
    "customOn": {
      bind(el, binding, vnode){
        if(typeof binding.value == "function"){
          let event = binding.arg;
          el.addEventListener(event, ()=>{
            el.innerHTML = binding.value();
          })
        }else{
          console.log('not a function');
        }
      }

    }
  }
};
</script>

<style>
</style>
