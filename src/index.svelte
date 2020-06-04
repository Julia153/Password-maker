<script>
//setting all of the numbers i use throughout my code as a varible so you know what they mean and they arent just random numbers
  const userMaxLength = 20;
  const userMinLength = 4;
  const numsInAlphabet = 26;
  const startNumLCL = 97;
  const numOfNums = 10;
  const startNumUCL = 65;
  const startNumNum = 48;
  const startNumSC = 35;
  const NumOfSC = 4;
  //setting all of my varibles
  let userLength = "";
  let userSC = false;
  let userLowerLetters = false;
  let userUpperletters = false;
  let userNumbers = false;
  let output = "";
  let checkboxesArray = [];
  //my function which connects to my button
  function makePassword() {
    //resetting the output as empty
    output = "";
    //if the user enters a number higher than 20 ask them toenter a lower number
    while (userLength > userMaxLength) {
      output = "Please enter a number of charcters that is less than 20";
      
      //if the user enters a number smaller than 4 tell them they need to enter a higher number
    } while (userLength < userMinLength) {
      output = "Please enter a number of charcters that is more than 4";
      
     
      //if the user chooses no check boxes, tell them to select at least 1
    } while (
      !userLowerLetters &&
      !userNumbers &&
      !userSC &&
      !userUpperletters
  ) {
      output = "Click at least one checkbox";
      
      
    } 
    //call the next function hich is the one which actually creates the password
    PasswordCreater();
  }
//function which creates the password
  function PasswordCreater() {
    //while the output length is smaller than the length the user choose keep going through this loop
    while (output.length < userLength) {
      //if the user choose the lowercase letters check box, add that to the arrary
      if (userLowerLetters) {
        checkboxesArray.push("LowerCaseLetters");
      }
      //if the user chose the upper case letters checkbox then add that to the arrary
      if (userUpperletters) {
        checkboxesArray.push("UpperCaseLetters");
      }
      //if the user chose the numbers checkbox, add that to the arrary
      if (userNumbers) {
        checkboxesArray.push("Numbers");
      }
      //if the user chose the special charcters check box, add that to the arrary
      if (userSC) {
        checkboxesArray.push("SpecialCharcters");
      }
      //choose a random item from the arrary of what ever checkboxes they choose
      let random =
        checkboxesArray[Math.floor(Math.random() * checkboxesArray.length)];
        // if the random generator choose lowercase letters, then add a random lowercase letter to the password
      if (random === "LowerCaseLetters") {
        let choiceInNumForLCL =
          Math.floor(Math.random() * numsInAlphabet) + startNumLCL;
        output += String.fromCharCode(choiceInNumForLCL);
        //is the random generator thingy chose the uppercase letter then add a random upper case letter to the password
      } else if (random === "UpperCaseLetters") {
        let choiceInNumForUCL =
          Math.floor(Math.random() * numsInAlphabet) + startNumUCL;
        output += String.fromCharCode(choiceInNumForUCL);
        //if the random number generator chose numbers from the arrary, add a random number between 1 and 10 to the password
      } else if (random === "Numbers") {
        let choiceInNumForN = Math.floor(Math.random() * numOfNums) + startNumNum;
        output += String.fromCharCode(choiceInNumForN);
        // and lastly if the random number generator chose the special charcters from the array then choose a random special charcter and add it to the password
      } else if (random === "SpecialCharcters") {
        let choiceInNumForSC = Math.floor(Math.random() * NumOfSC) + startNumSC;
        output += String.fromCharCode(choiceInNumForSC);
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
<!--This is a couple of titles and a very short info bit about this page and what you do on it-->
  <h1>Password Maker</h1>

  <p>Create a secure password!</p>

  <h2>Choose your contents:</h2>
  <!--the input section where the user can choose how long they want their password to be from 4 to 20-->
  <label>
    How many charcters do you want your password to be?
    <input
      class="input"
      type="number"
      min="1"
      max="20"
      bind:value={userLength} />
  </label>
  <!--a checkbox for the user to choose if they want lowercase letters in their password or not-->
  <label>
    Lowercase Letters:
    <input
      id="lowerLettersCheckbox"
      class="checkbox"
      type="checkbox"
      bind:checked={userLowerLetters} />
  </label>
  <!--another checkbox to see if the user wants to have upper case letters in their code or not-->
  <label>
    Uppercase Letters:
    <input
      id="UpperLettersCheckbox"
      class="checkbox"
      type="checkbox"
      bind:checked={userUpperletters} />
  </label>
  <!--the third checkbox to see if the user wants to have number in their password or not-->
  <label>
    Numbers
    <input
      id="NumbersCheckbox"
      class="checkbox"
      type="checkbox"
      bind:checked={userNumbers} />
  </label>
  <!--The last checkbox to see if the user wants to have scpecial charcter in their code or not-->
  <label>
    Special Charcters:
    <input
      id="SpecialCharctersCheckbox"
      class="checkbox"
      type="checkbox"
      bind:checked={userSC} />
  </label>
  <!--This is a space, so my page looks nicer :)-->
  <br />
  <!--A button to press which runs the function to make the password when the user is ready-->
  <button class="button" on:click={makePassword}>Make Password!</button>
  <!--Gives the user their password!-->
  <p>Here is your password:</p>
  <p>{output}</p>
</section>
