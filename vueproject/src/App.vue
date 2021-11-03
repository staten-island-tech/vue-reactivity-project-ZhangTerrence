<template>
  <section id="app">
    <h1 id="title">{{title}}</h1>
    <div id="main">
      <div id="burger">
        <div class="topbun"></div>
        <div id="toppingsection"></div>
        <div class="botbun"></div>
      </div>
      <div id="topping">
        <div class="toppingcontainer">
          <div class="toppinginfo" v-for="(topping, key) in toppings" :key="key">
            <h1 class="toppingname">{{topping.name}}</h1>
            <div class="buttondiv">
              <button id="add" :class="topping.name" v-on:click="add">Add</button>
              <button id="remove" :class="topping.name" v-on:click="remove">Remove</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "app",
  data(){
    return{
      title: "Borger Builder",
      toppings: [{
        name: "Steak",
      }
      ,
      {
        name: "Chicken",
      }
      ,
      {
        name: "Cheese",
      }
      ,
      {
        name: "Lettuce",
      }
      ,
      {
        name: "Bacon",
      }
      ,
      {
        name: "Tomato",
      }
      ,
      ]
    }
  },
  methods: {
    add: function(e){
      const element = e.srcElement;
      const requestTopping = element.classList[0]
      const addedTopping = document.createElement("div")
      addedTopping.classList.add(requestTopping)
      document.getElementById("toppingsection").appendChild(addedTopping)
    },
    remove: function(e){
      const element = e.srcElement;
      const requestTopping = element.classList[0]
      const check = document.getElementsByClassName(requestTopping)
      const select = check[0]
      if (select.tagName === "DIV"){
        select.remove()
      }
    }
  }
}
</script>

<style>
::-webkit-scrollbar {
  width: 10px;
}
::-webkit-scrollbar-track {
  box-shadow: inset 0 0 5px grey;
  border-radius: 10px;
}
::-webkit-scrollbar-thumb {
  background: grey;
  border-radius: 10px;
}
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-size: 62.5%;
}
section{
  width: 100vw;
  height: 100vh;
}
#title{
  width: 100vw;
  height: 10vh;
  font-size: 5rem;
  display: flex;
  justify-content: center;
  align-items: center;
  border: 1px solid black;
}
#main{
  width: 100vw;
  height: 90vh;
  display: flex;
  flex-direction: row;
}
#burger{
  width: 80vw;
  height: 90vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 10px;
}
.topbun{
  width: 35rem;
  height: 10rem;
  border-radius: 100% 100% 0 0;
  background-color: rgb(177, 89, 30);
  box-shadow: inset -12.5px 0 rgb(182, 73, 0);
}
#toppingsection{
  width: 80vw;
  height: 70vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.botbun{
  width: 35rem;
  height: 10rem;
  border-radius: 0 0 100% 100%;
  background-color: rgb(177, 89, 30);
  box-shadow: inset -12.5px 0 rgb(182, 73, 0);
}
.Steak{
  width: 35rem;
  height: 5rem;
  background-color: brown;
  border-radius: 20px;
  border: 2.5px solid black;
}
.Lettuce{
  width: 35rem;
  height: 2.5rem;
  background-color: greenyellow;
  border-radius: 20px;
  border: 2.5px solid black;
}
.Cheese{
  width: 35rem;
  height: 1.5rem;
  background-color: gold;
  border-radius: 20px;
  border: 2.5px solid black;
}
.Bacon{
  width: 35rem;
  height: 1.5rem;
  background-color: rgb(212, 45, 45);
  border-radius: 20px;
  border: 2.5px solid black;
}
.Tomato{
  width: 35rem;
  height: 4rem;
  background-color: red;
  border-radius: 20px;
  border: 2.5px solid black;
}
.Chicken{
  width: 35rem;
  height: 5rem;
  background-color: rgb(214, 181, 31);
  border-radius: 20px;
  border: 2.5px solid black;
}
#topping{
  width: 20vw;
  height: 90vh;
  overflow-y: scroll;
}
.toppingcontainer{
  height: 180vh;
}
.toppinginfo{
  height: 30vh;
  border: 1px solid black;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.toppingname{
  height: 10vh;
  width: 100%;
  background-color: pink;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-size: 2.5rem;
}
.buttondiv{
  width: 100%;
  height: 20vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-evenly;
}
#add{
  width: 80%;
  height: 8vh;
  font-size: 2.5rem;
}
#remove{
  width: 80%;
  height: 8vh;
  font-size: 2.5rem;
}
</style>
