<script>
    const userMaxLength = 20
    const userMinLength = 4

    let userLength = ''
    let userSC = false
    let userLowerLetters = false
    let userUpperletters = false
    let userNumbers = false
    let output = ''
    let password = ''
    
    function makePassword() {
        let counter = 0
         if (userLength > userMaxLength) {
             output = "Please enter a number of charcters that is less than 20"
         } else if (userLength < userMinLength) {
             output = "Please enter a number of charcters that is more than 0"
         } else if (!userLowerLetters && !userNumbers && !userSC && !userUpperletters) {
             output = "Click at least one checkbox"
         } else if (userLowerLetters && !userUpperletters && !userNumbers && !userSC) {
             while (counter < userLength) {  
                let choiceInNumbers = Math.floor(Math.random() * 26) + 97
                output += String.fromCharCode(choiceInNumbers)
                counter ++
             } if (counter > userLength) {
                 console.log(password)
                output = password
                password = ''
                counter = 0
             }
             console.log(output)
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
How many charcters do you want your password?<input class="input" type="number" min="1" max="20" bind:value={userLength}>
</label>
<label>
Lowercase Letters:<input id="lowerLettersCheckbox" class="checkbox"type="checkbox" bind:checked={userLowerLetters}>
</label>
<label>
Uppercase Letters:<input id="UpperLettersCheckbox" class="checkbox" type="checkbox" bind:checked={userUpperletters}>
</label>
<lable>
Numbers:<input id="numbersCheckbox" class="checkbox" type="checkbox" bind:checked={userNumbers}>
</lable>
<label>
Special Charcters:<input id="SpecialCharctersCheckbox" class="checkbox"type="checkbox" bind:checked={userSC}>
</label>
<br>
<button class="button" on:click={makePassword}>Make Password!</button>
<p>Here is your password:</p>
<p>{output}</p>
</section>