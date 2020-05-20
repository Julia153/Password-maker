<script>
    let userLength = ''
    let password = ''
    let userSC = false
    let userLetters = false
    let userNumbers = false
    
    function makePassword() {
         if (userLength > 20) {
             password = "Please enter a number of charcters that is less than 20"
         } else if (userLength < 1) {
             password = "Please enter a number of charcters that is more than 0"
         } else if (!userLetters && !userNumbers && !userSC ) {
             password = "Click at least one checkbox"
         }
    }
</script>
<style>
    label {
        padding: 10px;
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
<br>
<label>
Letters:<input id="lettersCheckbox" class="checkbox"type="checkbox" bind:checked={userLetters}>
</label>
<lable>
Numbers:<input id="numbersCheckbox" class="checkbox" type="checkbox" bind:checked={userNumbers}>
</lable>
<label>
Special Charcters:<input id="SpecialCharctersCheckbox" class="checkbox"type="checkbox" bind:checked={userSC}>
</label>
<br>
<button class="button" on:click={makePassword}>Make Password!</button>
<br>
<br>
<p>Here is your password:</p>
<p>{password}</p>
</section>