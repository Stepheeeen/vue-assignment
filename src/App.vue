<script>
export default {
  data() {
    return {
      randomNum: 0,
      inputedValue: null,
      isCorrect: undefined,
    };
  },
  methods: {
    onClick() {
      if (+this.randomNum === +this.inputedValue) {
        this.isCorrect = true;
      } else {
        this.isCorrect = false;
        this.inputedValue = null;
      }
      this.generateValue();
    },
    generateValue() {
      const min = 1;
      const max = 10;
      const randomNumber = Math.floor(Math.random() * (max - min + 1)) + min;
      this.randomNum = randomNumber;
    },
  },
  mounted() {
    this.generateValue();
  },
};
</script>

<template>
  <main>
    <div id="container">
      <div class="random-gen">
        <h2>Guess a number between 0 - 9</h2>

        <input
          type="number"
          name="input"
          id="random-nuber"
          v-model="inputedValue"

          @keyup.enter="onClick"
        />
        <button @click="onClick">Check</button>

        <p v-show="isCorrect" class="correct">Correct !!</p>
        <p v-show="isCorrect === false" class="wrong">
          Wrong! Answer is {{ randomNum }}
        </p>
      </div>
    </div>
  </main>
</template>

<style>
body::-webkit-scrollbar{
  display: none;
}
main {
 display: grid;
 place-items: center;
 width: 100%;
 height: 100vh;
}
#container {
  padding: 20px;
  border: 2px solid #333;
  border-radius: 20px;
}

.random-gen input {
  width: 100%;
  height: 30px;
  border: 2px solid #000000;
  margin: 10px 0;
  background: #fff;
  color: #222;
  padding-left: 10px;
  margin-left: -5px;
}
.random-gen button{
  margin-top: 10px;
  border: none;
  padding: 10px 30px;
  background: #182ef3;
  color: #fff;
  border-radius: 5px;
}
</style>
