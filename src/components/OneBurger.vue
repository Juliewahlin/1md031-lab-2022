<template>
    <div>
      <!--{{ burger.name }} {{ burger.kCal }}-->
        
        <h3>
          {{ burger.name }}
        </h3>
        <img v-bind:src="burger.url" style="width:300px; height:300px">
        <div> <h3>Innehåller:</h3>       
          <ul>
          <li> {{ burger.kCal }} kCal</li>
          <li> Laktos: {{burger.lactose}} </li>
          <li> Gluten: {{burger.gluten}}</li>
        </ul> 
        <div id="button">
          <button v-on:click="IncreaseBurger">
            Add to order!
          </button>
        </div>

        <div id="button">
          <button v-on:click="DecreaseBurger">
            Take away from order!
          </button>
        </div>
      </div>


    </div>
</template>
  
  <script>
  export default {
    name: 'OneBurger',
    props: {
      burger: Object
    },

    data:function(){
      return{amountOrdered:0,}
    },

    methods:{
      IncreaseBurger:function(){
        this.amountOrdered=this.amountOrdered+1
        this.$emit('orderedBurgers', { name: this.burger.name, 
                                  amount: this.amountOrdered 
                              }
                              );
                            },

      DecreaseBurger:function(){
       if (this.amountOrdered >0){
         this.amountOrdered=this.amountOrdered-1}
         this.$emit('orderedBurgers', { name: this.burger.name, 
                                  amount: this.amountOrdered 
                              }
                              );
                            }

    }

  }
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>
  
  </style>
  