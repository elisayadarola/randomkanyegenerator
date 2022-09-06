<template>
  <div class="changes">
    <h1 class="text-3xl font-bold underline border-solid mb-20px">{{ msg }}</h1>
    <img :src="picture" :alt="`${name.first} ${name.last}`" />
    <h3>"{{ quote }}"</h3>
    <button @click="getQuote()">
      👆 Click to get your random Kanye quote!👆
    </button>
    <!-- <div>
      <img :src="picture" :alt="`${name.first} ${name.last}`" />
    </div>
    <button @click="getImg()">click me</button> -->
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      quote: " I'm gonna buy Earth",
      picture:
        "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRssZsjz642rYuvvd9Z5n4BkTl9x7q0lhOZNA&usqp=CAU",
      name: {
        title: "mr",
        first: "Kanye",
        last: "West",
      },
    };
  },
  /*Aqui no me dejaba hacer lo mismo que en el video de traversy media, porque
  el tipo desestructuró los resultado, yo no necesito. 
  Y despues tambien ponia [0] porque a eldbia devolver un obejto. a mi no. 
  Al quitarlo y poner data.quote, resolvi el problema*/
  methods: {
    async getQuote() {
      const res = await fetch("https://api.kanye.rest");
      const data = await res.json();
      console.log(data);
      this.quote = data.quote;
    },
    async getImg() {
      const res_2 = await fetch("https://random.imagecdn.app/500/150");
      const data_2 = res_2.json;
      this.picture = data_2;
      console.log("hello");
    },
  },
  // async getImg() {
  //   const res_2 = await fetch("https://random.imagecdn.app/500/150");
  //   const img_2 = res_2.json();
  //   this.picture = img_2;
  //   console.log("hello");
  // },
};
</script>


<style scoped>
div {
  border: solid red 1px;
  padding-bottom: 4rem;
  width: 50%;
  /* margin: 25vh; */
  justify-content: center;
  /* display: flex;
  justify-content: center; */
  margin: auto auto;
}
div,
h1,
h3 {
  align-items: center;
  justify-content: center;
  display: block;
  background-color: rgb(255, 196, 0);
}
img {
  border-radius: 10%;
  background-color: rgb(232, 208, 21);
  /* box-shadow: 30px lightblue; */
  margin-top: 10px;
  width: 50%;

  height: auto;
  box-shadow: inset 0 0 50px rgb(255, 255, 255),
    /* inner white */ inset 20px 0 80px rgb(25, 0, 255),
    /* inner left magenta short */ inset -20px 0 80px rgb(30, 0, 255),
    /* inner right cyan short */ inset 20px 0 300px rgb(34, 0, 255),
    /* inner left magenta broad */ inset -20px 0 300px rgb(76, 0, 255),
    /* inner right cyan broad */ 0 0 50px #fff,
    /* outer white */ -10px 0 80px rgb(93, 0, 255),
    /* outer left magenta */ 10px 0 80px rgb(17, 0, 255);
}

h1 {
  color: rgb(18, 18, 92);

  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
}
h3 {
  margin-top: 3rem;
  color: rgb(33, 33, 215);
  font-size: larger;
  text-decoration: underline;
}
button {
  background-color: rgb(45, 45, 146);
  color: white;
  padding: 10px;
  font-weight: bold;
  font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
    "Lucida Sans Unicode", Geneva, Verdana, sans-serif;

  /* margin-bottom: 5rem; */
}
button:hover {
  background-color: white;
  font: bolder;
  color: rgb(45, 45, 146);
  padding: 15px;
}
</style>
