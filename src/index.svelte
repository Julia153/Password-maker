<script>
  const userMaxLength = 20;
  const userMinLength = 4;

  let userLength = "";
  let userSC = false;
  let userLowerLetters = false;
  let userUpperletters = false;
  let userNumbers = false;
  let output = "";
  let password = "";
  let numOfBox = 0;

  function makePassword() {
    output = "";
    if (userLength > userMaxLength) {
      output = "Please enter a number of charcters that is less than 20";
    } else if (userLength < userMinLength) {
      output = "Please enter a number of charcters that is more than 0";
    } else if (
      !userLowerLetters &&
      !userNumbers &&
      !userSC &&
      !userUpperletters
    ) {
      output = "Click at least one checkbox";
    }
    lengthPasswordCreater();
  }

  function lengthPasswordCreater() {
    for (let i = 0; i < userLength; i++) {
      if (userLowerLetters) {
        numOfBox++
        let choiceInNumbersForLowerLetters =
          Math.floor(Math.random() * 26) + 97;
        output += String.fromCharCode(choiceInNumbersForLowerLetters);
        console.log(output);
      } if (userUpperletters) {
        numOfBox++
        let choiceInNumbersForUpperLetters =
          Math.floor(Math.random() * 26) + 65;
        output += String.fromCharCode(choiceInNumbersForUpperLetters);
      } if (userNumbers) {
        numOfBox++
        let choiceInNumbersForNumbers = Math.floor(Math.random() * 10) + 48;
        output += String.fromCharCode(choiceInNumbersForNumbers);
      } if (userSC) {
        numOfBox++
        let choiceInNumbersForSC = Math.floor(Math.random() * 4) + 35;
        output += String.fromCharCode(choiceInNumbersForSC);
      }
    }
  }
</script>

<style>
  label {
    padding: 10px;
  }

  button {
    display: block;
  }
</style>

<!--HTML-->
<section class="section content">
  <h1>Password Maker</h1>

  <p>Create a secure password!</p>

  <h2>Choose your contents:</h2>
  <label>
    How many charcters do you want your password?
    <input
      class="input"
      type="number"
      min="1"
      max="20"
      bind:value={userLength} />
  </label>
  <label>
    Lowercase Letters:
    <input
      id="lowerLettersCheckbox"
      class="checkbox"
      type="checkbox"
      bind:checked={userLowerLetters} />
  </label>
  <label>
    Uppercase Letters:
    <input
      id="UpperLettersCheckbox"
      class="checkbox"
      type="checkbox"
      bind:checked={userUpperletters} />
  </label>
  <lable>
    Numbers:
    <input
      id="numbersCheckbox"
      class="checkbox"
      type="checkbox"
      bind:checked={userNumbers} />
  </lable>
  <label>
    Special Charcters:
    <input
      id="SpecialCharctersCheckbox"
      class="checkbox"
      type="checkbox"
      bind:checked={userSC} />
  </label>
  <br />
  <button class="button" on:click={makePassword}>Make Password!</button>
  <p>Here is your password:</p>
  <p>{output}</p>
</section>
