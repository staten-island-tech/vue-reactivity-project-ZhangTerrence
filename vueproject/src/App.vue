<template>
  <section id="app">
    <h1 id="title">{{ title }}</h1>
    <div id="main">
      <div id="burgerdiv" v-on:dragover="drop">
        <div id="botbun" class="draggable"></div>
        <div id="topbun" class="draggable"></div>
      </div>
      <div id="toppingdiv">
        <div class="wrapper">
          <div class="toppings">
            <div class="toppinginfo" v-for="(topping, index) in toppings" :key="index">
              <h1 id="name">{{ topping.name }}</h1>
              <div :id="topping.name" class="container">
                <div
                  :class="topping.name"
                  draggable="true"
                  class="draggable"
                  v-on:dragstart="start"
                  v-on:dragend="end"
                ></div>
              </div>
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
  data() {
    return {
      title: "Borger Builder",
      toppings: [
        {
          name: "Tomato",
        },
        {
          name: "Cheese",
        },
        {
          name: "Lettuce",
        },
        {
          name: "Onion",
        },
        {
          name: "Bacon",
        },
        {
          name: "Food",
        },
        {
          name: "Stuff",
        },
        {
          name: "More",
        },
      ],
    };
  },
  methods: {
    start: function (e) {
      const element = e.srcElement;
      element.classList.add("dragging");
    },
    end: function (e) {
      const element = e.srcElement;
      /* function cloning(){
        const origin = element.classList[0]
        const originElement = document.getElementById(origin)
        const clone = document.createElement("div")
        clone.draggable = true
        clone.classList.add(`${origin}`)
        clone.addEventListener("dragstart", ()=>{
          clone.classList.add("dragging");
        })
        clone.addEventListener("dragend", ()=>{
          clone.draggable = true
          clone.classList.add(`${origin}`)
          clone.classList.remove("dragging")
        })
        clone.addEventListener("click", ()=>{
          clone.remove()
        })
        originElement.appendChild(clone)
      } 
      cloning() */
      element.classList.remove("dragging");
    },

    drop: function (e) {
      e.preventDefault();
      const containerElement = e.srcElement;
      const dragg = document.querySelectorAll(".dragging")[0];
      if (containerElement != document.getElementById("topbun") && containerElement != document.getElementById("botbun")){
        containerElement.appendChild(dragg)
      }
    }
  },
  mounted: function test(){
    const allDrags = document.getElementsByClassName("draggable")
    for (const elmnt in allDrags){
      const movable = allDrags[elmnt];
      movable.addEventListener("click", ()=>{
        console.log("hi");
      })
    }
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Londrina+Solid&display=swap");
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
#title {
  font-size: 5rem;
  font-family: "Londrina Solid", cursive;
  padding-top: 0.5rem;
  height: 10vh;
  margin: 0;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-content: center;
}
#main {
  height: 90vh;
  width: 100vw;
  display: flex;
  flex-direction: row;
}
#toppingdiv {
  width: 20vw;
  overflow: hidden;
  position: relative;
  justify-content: space-evenly;
}
#burgerdiv {
  width: 80vw;
  border: 1px solid black;
  display: flex;
  flex-direction: column-reverse;
  
}
.wrapper {  
  height: 90vh;
  overflow: scroll;
  overflow-y: overlay;
  overflow-x: overlay;
}
.toppings {
  height: 240vh;
  display: flex;
  flex-direction: column;
  align-content: center;
  justify-content: space-evenly;
}
.toppinginfo {
  height: 30vh;
  font-size: 5rem;
  border: black 1px solid;
  display: flex;
  flex-direction: column;
}
#name {
  height: 25%;
  font-size: 5rem;
  display: flex;
  align-items: center;
  justify-content: center;
}
.container {
  height: 90vh;
  display: flex;
  flex-direction: column;
  height: 75%;
  width: 75%;
}
.Tomato {
  width: 20rem;
  height: 2.5rem;
  border-radius: 10% 10% 10% 10%;
  background-color: red;
}
.Cheese {
  width: 20rem;
  height: 0.5rem;
  background-color: gold;
}
#topbun {
  height: 10rem;
  width: 50rem;
  border-radius: 100% 100% 0 0;
  background-color: rgb(133, 86, 12);
}
#botbun {
  height: 10rem;
  width: 50rem;
  border-radius: 0 0 100% 100%;
  background-color: rgb(133, 86, 12);
}
.draggable.dragging {
  opacity: 50%;
}
#final {
  height: 10vh;
}
</style>
