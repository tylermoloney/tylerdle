<template>
  <div id="board">
    <h1>Tylerdle</h1>
    <p>Guess the word in 6 tries.</p> 
    <p>A <span class="correct">green</span> letter is correct and in the correct position.</p> 
    <p>A <span class="present">yellow</span> letter is in the word but not in that position.</p> 
    <p>A <span class="absent">grey</span> letter is not in the word at all.</p> 
    <p>This uses past solutions from <a href="https://www.nytimes.com/games/wordle/index.html" target=":blank">Wordle</a> so no worries about spoilers from future puzzles!</p>
    <div class="row" id="row1">
      <div class="letter" id="11"></div>
      <div class="letter" id="12"></div>
      <div class="letter" id="13"></div>
      <div class="letter" id="14"></div>
      <div class="letter" id="15"></div>
    </div>
    <div class="row" id="row2">
      <div class="letter" id="21"></div>
      <div class="letter" id="22"></div>
      <div class="letter" id="23"></div>
      <div class="letter" id="24"></div>
      <div class="letter" id="25"></div>
    </div>
    <div class="row" id="row3">
      <div class="letter" id="31"></div>
      <div class="letter" id="32"></div>
      <div class="letter" id="33"></div>
      <div class="letter" id="34"></div>
      <div class="letter" id="35"></div>
    </div>
    <div class="row" id="row4">
      <div class="letter" id="41"></div>
      <div class="letter" id="42"></div>
      <div class="letter" id="43"></div>
      <div class="letter" id="44"></div>
      <div class="letter" id="45"></div>
    </div>
    <div class="row" id="row5">
      <div class="letter" id="51"></div>
      <div class="letter" id="52"></div>
      <div class="letter" id="53"></div>
      <div class="letter" id="54"></div>
      <div class="letter" id="55"></div>
    </div>
    <div class="row">
      <div class="letter" id="61"></div>
      <div class="letter" id="62"></div>
      <div class="letter" id="63"></div>
      <div class="letter" id="64"></div>
      <div class="letter" id="65"></div>
    </div>
    <br />
    <div class="keyboard">
      <div class="keyboardrow">
          <button v-on:mousedown="this.addLetter($event)" id="qkey">
          Q
        </button>
        <button
          v-on:mousedown="this.addLetter($event)" id="wkey">
          W
        </button>
        <button
          v-on:mousedown="this.addLetter($event)" id="ekey">
          E
        </button>
        <button
          v-on:mousedown="this.addLetter($event)"
          id="rkey"
        >
          R
        </button>
        <button
          v-on:mousedown="this.addLetter($event)"
          id="tkey"
        >
          T
        </button>
        <button
          v-on:mousedown="this.addLetter($event)"
          id="ykey"
        >
          Y
        </button>
        <button
          v-on:mousedown="this.addLetter($event)"
          id="ukey"
        >
          U
        </button>
        <button
          v-on:mousedown="this.addLetter($event)"
          id="ikey"
        >
          I
        </button>
        <button
          v-on:mousedown="this.addLetter($event)"
          id="okey"
        >
          O
        </button>
        <button
          v-on:mousedown="this.addLetter($event)"
          id="pkey"
        >
          P
        </button>
      </div>
      <div class="keyboardrow">
        <button
          v-on:mousedown="this.addLetter($event)"
          id="akey"
        >
          A
        </button>
        <button
          v-on:mousedown="this.addLetter($event)"
          id="skey"
        >
          S
        </button>
        <button
          v-on:mousedown="this.addLetter($event)"
          id="dkey"
        >
          D
        </button>
        <button
          v-on:mousedown="this.addLetter($event)"
          id="fkey"
        >
          F
        </button>
        <button
          v-on:mousedown="this.addLetter($event)"
          id="gkey"
        >
          G
        </button>
        <button
          v-on:mousedown="this.addLetter($event)"
          id="hkey"
        >
          H
        </button>
        <button
          v-on:mousedown="this.addLetter($event)"
          id="jkey"
        >
          J
        </button>
        <button
          v-on:mousedown="this.addLetter($event)"
          id="kkey"
        >
          K
        </button>
        <button
          v-on:mousedown="this.addLetter($event)"
          id="lkey"
        >
          L
        </button>
      </div>
      <div class="keyboardrow">
        <button v-on:mousedown="this.submitWord()" id="enterkey">ENTER</button>
        <button
          v-on:mousedown="this.addLetter($event)"
          id="zkey"
        >
          Z
        </button>
        <button
          v-on:mousedown="this.addLetter($event)"
          id="xkey"
        >
          X
        </button>
        <button
          v-on:mousedown="this.addLetter($event)"
          id="ckey"
        >
          C
        </button>
        <button
          v-on:mousedown="this.addLetter($event)"
          id="vkey"
        >
          V
        </button>
        <button
          v-on:mousedown="this.addLetter($event)"
          id="bkey"
        >
          B
        </button>
        <button
          v-on:mousedown="this.addLetter($event)"
          id="nkey"
        >
          N
        </button>
        <button
          v-on:mousedown="this.addLetter($event)"
          id="mkey"
        >
          M
        </button>
        <button v-on:mousedown="this.playerWord = this.playerWord.substring(0, this.playerWord.length - 1); this.clearRow(); this.fillWord();" id="backspacekey">
          <svg xmlns="http://www.w3.org/2000/svg" height="24" viewBox="0 0 24 24" width="24">
            <path d="M22 3H7c-.69 0-1.23.35-1.59.88L0 12l5.41 8.11c.36.53.9.89 1.59.89h15c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zm0 16H7.07L2.4 12l4.66-7H22v14zm-11.59-2L14 13.41 17.59 17 19 15.59 15.41 12 19 8.41 17.59 7 14 10.59 10.41 7 9 8.41 12.59 12 9 15.59z">
            </path>
          </svg>
        </button>
      </div>
    </div>
    <div id="refresh" v-show="!gameActive">
      <p>Refresh this page to get a new puzzle!</p>
    </div>
    <div class="socials">
      <a href="https://www.linkedin.com/in/tyler-moloney" target=":blank"><img src="https://cdn-icons-png.flaticon.com/512/61/61109.png" alt="LinkedIn Icon" class="socialicon"></a>
      <a href="https://www.github.com/tylermoloney" target=":blank"><img src="https://cdn-icons-png.flaticon.com/512/25/25231.png" alt="github icon" class="socialicon"></a>
      <p>By Tyler Moloney</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      playerWord: "",
      wordArray: [],
      guessCount: 1,
      allowedGuesses: [],
      puzzleWord: String,
      puzzleArray: [],
      gameActive: Boolean,
      letterMap: Map,
      alphabet: [
        "a",
        "b",
        "c",
        "d",
        "e",
        "f",
        "g",
        "h",
        "i",
        "j",
        "k",
        "l",
        "m",
        "n",
        "o",
        "p",
        "q",
        "r",
        "s",
        "t",
        "u",
        "v",
        "w",
        "x",
        "y",
        "z",
      ],
    };
  },
  created() {
    this.allowedGuesses = require(`../assets/allowedguesses.json`);
    var potentialArray = require(`../assets/potentialPuzzles.json`);
    this.puzzleWord = potentialArray[Math.floor(Math.random() * (potentialArray.length -1))];
    this.puzzleWord = this.puzzleWord.toUpperCase();
    this.puzzleArray = this.puzzleWord.split("");
    this.gameActive = true;
    this.playerWord = "";
  },
  methods: {
    addLetter(event){
      var letter = event.target.id.substring(0,1)
      this.playerWord += letter
      this.fillWord();
    },
    clearRow() {
      for (var i = 1; i <= 5; i++) {
        var letterId = "" + this.guessCount + i;
        var documentId = document.getElementById(letterId);
        documentId.innerText = "";
      }
    },
    fillWord() {
      //put the player's word in the game board
      this.playerWord = this.playerWord.toUpperCase();
      this.wordArray = this.playerWord.split("");
      for (var i = 1; i <= this.wordArray.length; i++) {
        var letterId = "" + this.guessCount + i;
        var documentId = document.getElementById(letterId);
        documentId.innerText = this.wordArray[i - 1];
      }
    },
    submitWord() {
      this.playerWord = this.playerWord.toUpperCase();
      this.wordArray = this.playerWord.split("");

      //Creating a map to handle duplicate letters.
      this.letterMap = new Map();
      this.letterMap.set(this.puzzleArray[0], 1);
      for (var m = 1; m < this.puzzleArray.length; m++) {
        if (this.letterMap.has(this.puzzleArray[m])) {
          this.letterMap.set(
            this.puzzleArray[m],
            this.letterMap.get(this.puzzleArray[m]) + 1
          );
        } else {
          this.letterMap.set(this.puzzleArray[m], 1);
        }
      }

      //checks if a 5 letter string has been submitted
      if (this.wordArray.length != 5 || !this.allowedGuesses.includes(this.playerWord.toLowerCase())) {
        alert("Please enter a valid 5 letter word.");
        this.playerWord = "";
        this.clearRow();
      } else {

        //loop through the letters submitted by the user
        for (var i = 1; i <= this.wordArray.length; i++) {

          //identify the div based on the row(guess count) and position in the word
          var letterId = "" + this.guessCount + i;
          var documentId = document.getElementById(letterId);
          var keyboardId = document.getElementById("" + this.wordArray[i - 1].toLowerCase() + "key");


          //set the row on the board to the word submitted
          documentId.innerText = this.wordArray[i - 1];
          documentId.classList.add("shake");

          //check if the letter is in the correct spot
          if (this.wordArray[i - 1] == this.puzzleArray[i - 1].toUpperCase()) {
            documentId.classList.add("correct");
            keyboardId.classList.add("correct");

            //check how many instances of that letter are in the map. If the letter appears only once, remove it from the map, else decrement its value in the map.
            var letterCount = this.letterMap.get(this.puzzleArray[i - 1]);
            if (letterCount == 1) {
              this.letterMap.delete(this.puzzleArray[i - 1]);
            } else if (letterCount > 1) {
              this.letterMap.set(this.puzzleArray[i - 1], letterCount - 1);
            }
          }
        }

        for (var j = 1; j <= this.wordArray.length; j++) {
          letterCount = this.letterMap.get(this.puzzleArray[j - 1]);
          letterId = "" + this.guessCount + j;
          documentId = document.getElementById(letterId);
          keyboardId = document.getElementById(
            "" + this.wordArray[j - 1].toLowerCase() + "key"
          );

          //check if the letter exists in the word in another position
          if (
            this.wordArray[j - 1] != this.puzzleArray[j - 1].toUpperCase() &&
            this.letterMap.has(this.wordArray[j - 1])
          ) {
            if (this.letterMap.get(this.wordArray[j - 1]) == 0) {
              documentId.classList.add("absent");
            }

            if (this.letterMap.get(this.wordArray[j - 1]) > 0) {
              documentId.classList.add("present");
              keyboardId.classList.add("present");
              this.letterMap.set(this.wordArray[j - 1], letterCount - 1);
            }
          } else {
            documentId.classList.add("absent");
            keyboardId.classList.add("absent");
          }
        }

        //if player is correct, the game is over
        if (this.playerWord == this.puzzleWord) {
          this.gameActive = false;
          alert(
            "You got " +
              this.puzzleWord +
              " in " +
              this.guessCount +
              " guesses."
          );
        }

        //if player has not gotten the word, increment the guess count and clear their input
        this.guessCount++;
        this.playerWord = "";
        this.wordArray = [];

        //if player has not guessed the word after 6, the game is over.
        if (this.guessCount == 7 && this.gameActive != false) {
          this.gameActive = false;
          alert("Sorry! The word was: " + this.puzzleWord);
        }
      }
    },
  },
  mounted() {
    this.playerWord = "";
    this.wordArray = "";
    this.guessCount = 1;

    //event listeners for keystrokes
    window.addEventListener("keydown", (e) => {
      if (e.key == "Enter") {
        this.submitWord();
        this.playerWord="";

      } else if (e.key == "Backspace") {
        this.playerWord = this.playerWord.substring(0, this.playerWord.length - 1);
        this.clearRow();
        this.fillWord();

      } else if (this.alphabet.includes(e.key)) {
        this.playerWord += e.key;
        this.fillWord();
      }
    });
  },
};
</script>

<style>
.socials{
  background-color:blueviolet;
  position: fixed;
  border-top-left-radius: 20px;
  bottom: 0;
  right: 0;
  width: 150px;
  height: 75px;
  display:flex;
  flex-wrap: wrap;
  justify-content: center;

}
.socialicon{
  width: 50px;
  height: 50px;
  padding: 5px;
  
}
#board {
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  color: white;
}
.letter {
  border: 2px solid rgb(216, 212, 212);
  width: 50px;
  height: 50px;
  vertical-align: center;
  line-height: 50px;
}

.keyboardrow {
  display: flex;
  justify-content: center;
}

button {
  width: 2em;
  border-radius: 5px;
  
}
p{
  font-size: 1rem;
}

#backspacekey,
#enterkey {
  width: 100px;
  font-size: 0.75em;
}
.row {
  display: flex;
}
#header {
  color: white;
}

#refresh{
  font-size: 1rem;
}

.absent {
  background-color: darkgray;
  color: white;
}

.present {
  background-color: rgb(196, 196, 56);
  color: white;
}
.correct {
  background-color: green;
  color: white;
}

.shake {
  animation: shake 0.5s cubic-bezier(0.36, 0.07, 0.19, 0.97) both;
  transform: translate3d(0, 0, 0);
  backface-visibility: hidden;
  perspective: 1000px;
}

@keyframes shake {
  10%,
  90% {
    transform: translate3d(-1px, 0, 0);
  }

  20%,
  80% {
    transform: translate3d(2px, 0, 0);
  }

  30%,
  50%,
  70% {
    transform: translate3d(-4px, 0, 0);
  }

  40%,
  60% {
    transform: translate3d(4px, 0, 0);
  }
}

@media screen and (max-width: 940px) {
  .socials{
  background-color:blueviolet;
  position: fixed;
  border-top-left-radius: 20px;
  bottom: 0;
  right: 0;
  width: 150px;
  height: 75px;
  display:flex;
  flex-wrap: wrap;
  justify-content: center;
  z-index: -1;
}
  
}
</style>