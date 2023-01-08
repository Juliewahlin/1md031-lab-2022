<template>
  <div>
    <header>
    <div class="header">
      <img src="https://media.istockphoto.com/id/1355628976/sv/foto/pattern-with-classic-cheeseburger-french-fries-and-soda-drink-on-orange-and-blue-background.jpg?s=612x612&w=0&k=20&c=i5FGKOqaDGgXUXWKi5fgcpTRhN2V1qGdXtyz2phMW6s=" style="width: 100%;">
    </div>

    <h1 class="headerText">
      Välkommen till Burger Pub!
    </h1>
  </header>
       
  
  <section id="order">
    <div class="description"> 
      <h2>
        Välj din burgare:
      </h2>
            
      Klicka på den burgaren som du vill ha:
    </div> 

    <div class="parent">
      <Burger v-for="burger in burgers"
              v-bind:burger="burger" 
              v-bind:key="burger.name"
              v-on:orderedBurgers="addToOrder($event)"/>

      <!--<div id="food" class="div1">         
        <h3>
          En ostburgare
        </h3>
        <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcS6tqrowvHm-4VGUmo-ujvscWjMN4p3K090Ag&usqp=CAU" style="width: 300px;">
        <ul>
          <li> 500 kCal</li>
          <li> Innehåller <span id="allergies">Gluten</span></li>
          <li> Innehåller <span id="allergies">Laktos</span></li>
        </ul>         
      </div>

      <div id="food" class="div2">         
        <h3>
          En bacon- och ostburgare
        </h3>
        <img src="https://media.istockphoto.com/id/182436877/sv/foto/bacon-cheesburger.jpg?s=612x612&w=0&k=20&c=26WWvcaoFtz9z_RuykQE7y88jIxGOZWnReFl8QDdWa4=" style="width: 300px;">
        <ul>
          <li> 500 kCal</li>
          <li> Innehåller <span id="allergies">Gluten</span></li>
          <li> Innehåller <span id="allergies">Laktos </span></li>
        </ul>           
      </div>

      <div id="food" class="div3">
        <h3>
          Pommes
        </h3>
        <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTqie2XigoVvrmXII3u098fmFZOfJsSatMvTQ&usqp=CAU" style="width: 200px;">
        <ul>
          <li> 250 kCal</li>
        </ul>
      </div>-->

    </div>
  </section>

 
  <section id="contact" class="contactwindow">
    <div class="description">
      <h2>
        Information:
      </h2>
      Fyll in din information här nedan.
    </div>

    <form>
      <fieldset>
        <div><h4> Leverans information:</h4></div>
        <p>Fullname:</p>
            <input v-model="fullname" required="required" placeholder="Full Name" />
            <p>Email:</p>
            <input v-model="email" required="required" placeholder="E-mail adress" />


         <!--<label for="Fulltname">Full name</label><br>
          <input type="text" id="fullname" v-model="fn" required="required" placeholder="First and Last name"> -->
        <!--<p>
          <label for="E-mail">E-mail</label><br>
          <input type="email" id="email" v-model="em" required="required" placeholder="E-mail address">
        </p>-->
        <!--<p>
          <label for="Street"> Street</label><br>
          <input type="text" id="street" v-model="sn" required="required" placeholder="Street name">
        </p>-->
        <!--<p>
          <label for="House number"> House number</label><br>
          <input type="number" id="housenumber" v-model="hn" required="required" placeholder="House number">
        </p>-->
      
                        
        <div><h4>Betalnings information:</h4></div>
        <div>Select payment:</div>
        <select v-model="paymentSelected">
          <option disabled value="">Please select one</option>
          <option>Card</option>
          <option>Swish</option>
          <option>Klarna</option>
          <option>Paypal</option>
          <option>Your life</option>
        </select>
        <!--<p>
          <label for="Payment">Choose payment method: </label><br>
          <select id="payment" v-model="pmm">
            <option>Card</option>
            <option>Swish</option>
            <option>Klarna</option>
            <option>Paypal</option>
            <option>Your life</option>
          </select>
        </p>-->
                         
        <h4>Övrigt:</h4>
        <div>Choose your gender:</div>
        <input type="radio" id="Male" value="Male" v-model="genderPicked" />
        <label for="Male">Male</label>
        <input type="radio" id="Female" value="Female" v-model="genderPicked" />
        <label for="Female">Female</label>
        <input type="radio" id="Dont" value="Do not wish to provide" v-model="genderPicked" />
        <label for="Dont">Do not wish to provide</label><br>
        <!--<label for="Gender">Choose your gender:</label><br>
        <p>
          <input type="radio" id="Male" name="gender">
          <label for="Male">Male</label><br>

          <input type="radio" id="Female" name="gender">
          <label for="Female">Female</label><br>
          
          <input type="radio" id="Dont" name="gender" checked="checked">
          <label for="Dont">Do not wish to provide</label><br>
        </p>-->
        <!--<p>
          <label for="knowSomething">Do we need to know something:</label><br>
          <textarea id="knowSomething" name="ks" cols="50" rows="10"> </textarea>
        </p>-->

      </fieldset>
    </form>
  </section>

  
<div id="map">
    <div id="mapscroll" v-on:click="setLocation($event)">
      <div id="dots" v-bind:style="{position:'relative', background: 'url(' + require('../../public/img/polacks.jpg')+ ')' }">
                 <!--  <div id="dots" v-bind:style="{ background: 'url(' + require('../../public/img/polacks.jpg')+ ')'}"> -->  
                    <div v-bind:location="location" v-bind:style="{ left: this.location.x + 'px', top: this.location.y + 'px', position: 'absolute'}" v-bind:key="'dots'">
                      T
                    </div>
                </div>
      </div>
    </div>
  

  <div id="button">
    <button v-on:click="placeOrder">
    <img src="https://media.istockphoto.com/id/867053758/sv/vektor/markera-ikonen-vektor-symbol-gr%C3%B6n-bock-isolerad-p%C3%A5-vit-bakgrund-markerade-ikonen-eller-r%C3%A4tt.jpg?s=612x612&w=is&k=20&c=T45X0fjHwSAAJ1s49YQmBwtZ61-ZPeceUzr3ufSf_Kc=" style="width: 30px;">
    Skicka din beställning!
  </button>
</div>

  <hr>
  <footer id="footerText">
    Skapade av Julie Wåhlin, 2022
  </footer>
  </div>
</template>

<script>
import Burger from '../components/OneBurger.vue'
import io from 'socket.io-client'
import menu from '../assets/menu.json'

const socket = io();

//var arrayOfBurgers = [
 //{
    //name:"En ostburgare", kCal: 500, url: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcS6tqrowvHm-4VGUmo-ujvscWjMN4p3K090Ag&usqp=CAU", lactose: true, gluten:false,
 //},
 //{
    //name:"En bacon- och ostburgare", kCal: 800, url: "https://media.istockphoto.com/id/182436877/sv/foto/bacon-cheesburger.jpg?s=612x612&w=0&k=20&c=26WWvcaoFtz9z_RuykQE7y88jIxGOZWnReFl8QDdWa4=", lactose: true, gluten:true,
 //},
 //{
    //name:"Pommes", kCal: 200, url: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTqie2XigoVvrmXII3u098fmFZOfJsSatMvTQ&usqp=CAU", lactose:false, gluten:true,
 //},
//];

/*function MenuItem(name, kCal, image, lactose, gluten){
  this.productName = name;
  this.calories = kCal;
  this.pic = image;
  this.lactose;
  this.gluten;
  
}*/

export default {
  name: 'HomeView',
  components: {
    Burger
  },
  
  data: function () {
    return {
      burgers: menu,
      fullname:"",
      email:"",
      paymentSelected:"",
      genderPicked:"",
      orderedBurgers:{},
      location:{x: 0,
                y: 0
              }
    }
  },

  methods: {
    setLocation: function(event) {
      var offset = {x: event.currentTarget.getBoundingClientRect().left,
                    y: event.currentTarget.getBoundingClientRect().top};
      this.location.x = event.clientX-10-offset.x;
      this.location.y = event.clientY-10-offset.y ;
      console.log("setLocation function runs")
      console.log(this.location.x);
      console.log(this.location.y);
    },

    addToOrder: function (event) {
      this.orderedBurgers[event.name] = event.amount;
      console.log(this.orderedBurgers)
    },

  placeOrder: function() {
    console.log("Placing order")
    socket.emit("addOrder", { orderId: this.getOrderNumber(),
                              details: { x: this.location.x,
                                         y: this.location.y},
                              orderItems: this.orderedBurgers, 
                              customer: {
                                fullName: this.fullname, 
                                email: this.email,
                                payment: this.paymentSelected,
                                gender: this.genderPicked
                              },
                              customerFullName: this.fullName, 
                            }
               );
    console.log("My object: " , this.orderedBurgers);
  }, 

  setSelectedBurger: function(burgare) {
    this.selectedBurgers.push(burgare.name);
  },

    getOrderNumber: function () {
      return Math.floor(Math.random()*100000);
    },
     
    addOrder: function (event) {
      var offset = {x: event.currentTarget.getBoundingClientRect().left,
                    y: event.currentTarget.getBoundingClientRect().top};
      socket.emit("addOrder", { orderId: this.getOrderNumber(),
                                details: { x: event.clientX - 10 - offset.x,
                                           y: event.clientY - 10 - offset.y },
                                orderItems: [this.orderedBurgers]
                                
                              }
                 );
      this.location.x = event.clientX;
      this.location.y = event.clientY;
    }
  }
}
</script>

<style>
  @import 'https://fonts.googleapis.com/css2?family=Rubik+Bubbles&display=swap';
@import 'https://fonts.googleapis.com/css2?family=Ubuntu&display=swap';
@import 'https://fonts.googleapis.com/css2?family=Nunito&display=swap';
  
#map{
  width:500px;
  height:500px;
  overflow: scroll
}

#mapscroll {
    width: 1920px;
    height: 1078px;
    background: url("../../public/img/polacks.jpg");
    
  }

body {
    font-family: "Rubik Bubbles";
    background-color: #acdbe3;

}


.headerText{
    position: absolute;
    
    width: 100%;
    text-align: center;
    
    color: rgb(153, 7, 7);
    font-size: 6vw;
    margin-top:-300px;
    
   

}


.header{
    position:relative;
    opacity: 0.5;
}

.parent{
  display: grid;
    grid-template-columns: 33% 33% 33%;
    justify-items: center;

}

/*.div1{
    background-color: aliceblue;
    
}
.div2{
    background-color: rgb(170, 212, 248);
    
}
.div3{
    background-color: rgb(207, 229, 249);
    
}*/




#allergies{
    color: rgb(153, 7, 7);
    font-weight: bold;
}

/*#food{
    width: 300px;
}*/


#order{
    margin-top: 15px;
    border: 15px dotted gold;
    background-color: aquamarine;
    font-family: "Ubuntu";
    

}

.description{
    margin-left: 10px;
}

#contact{
    margin-top: 15px;
    border: 15px dotted gold;
    background-color: rgb(0, 255, 183);
    font-family: "Nunito";
    
}

#button{
    margin-top: 15px;
    margin-bottom: 15px;
}

button:hover {
    color: green;
    cursor: pointer;
 }


 #footerText{
    font-size: small;
 }
 


 @media screen and (max-width: 1000px){
    .headerText{
        position:fixed;
        font-size: 6vw;
        margin-top: -220px;
    }



}

</style>