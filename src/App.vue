<script>
export default {
  data(){ // data: function() { is de lange manier
    return {
      titel: 'Welkom in de Vue App',
      intro: 'Vue is echt een fantastisch framework.',
      imagePath: './src/assets/frieren.png',
      fullName: 'Tom Kellens',
      myAge: 23,
      newAge: 0,
      vueWebsite: 'https://vuejs.org/',
      buttonState: true,
    }
  },

  methods: {
    dynamicString: function() {

      if(this.giveRandomNumber() < 0.5) {
        return "Wij verkopen je de beste producten die je op de markt kan vinden";
      }
      else {
        return "Wie zoekt die vindt";
      }
    },
    myAgeAddFive: function() {
      return this.myAge + 5;
    },
    giveRandomNumber: function() {
      let randomNumber = Math.random();
      return randomNumber;
    },
    buttonShow() {
      this.buttonState = false;
    },
    buttonHide() {
      this.buttonState = true;
    },
    changeImagePath(event, path) {
      this.imagePath = path;
      event.target.innerText = "Afbeelding gewijzigd";
    }
  }
}
</script>

<template>
  <h1>{{ titel }}</h1>
  <p>{{ intro }}</p>
  <p>{{ dynamicString().toUpperCase() }}</p>

  <img @click="buttonShow()" :src="imagePath">
  <br>
  <button @click="buttonHide()" v-bind:hidden="buttonState">Verberg mij</button>

  <h2 @click="myAge += 1">{{ fullName }}</h2>
  <p>{{ myAgeAddFive() }}</p>
  <h1>{{ giveRandomNumber() }}</h1>
  <a :href="vueWebsite"></a>
  <input type="text" :value="fullName">
  <br>
  <button v-on:click="changeImagePath($event, './src/assets/fern.jpeg')">Verander image</button>
</template>

<style>
img {
  width: 25%;
}
</style>
