<template>
  <div class="home">
    <div class="container-fluid">
      <div class="row">
        <div class="col-lg-4"></div>
        <div class="col-lg-4">
          <center>
            <h1>Guessing game</h1>
            <div>
              To start, press Play. The program will generate a number between 1
              and 10. You have 3 tries to guess the number. Press Submit when you believe you have guessed the number.
            </div>
            <div>
              <button @click="generaterandom()">Play</button>
            </div>
            <div>
              Guesses remaining: {{guesses}}
            </div>
            <div>
              <label for="currentGuess">Enter your guess below</label> 
              <br>
              <input type="int" name="currentGuess" v-model="currentGuess">
            </div>
            <div>
              <button @click="submit()">Submit</button>
            </div>
            {{winState}}
          </center>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      toGuess:"",
      currentGuess:"",
      guesses:"",
      winState:"",
    };
  },
  methods: {
    submit(){
      if(this.toGuess==this.currentGuess){
        this.winState="You Win"
        return
      }
      if(this.guesses==1){
        this.guesses="1"
        this.winState = "You Lose"
      }
      if(this.guesses==0){
        return
      }
      this.guesses = this.guesses - 1;
    },
    generaterandom(){
      this.toGuess = Math.floor(Math.random() * 10 + 1);;
      this.guesses = 3;
    },
  },
};
</script>

<style scoped></style>
