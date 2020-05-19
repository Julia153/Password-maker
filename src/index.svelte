<script>
    let userLength = ''
    let password = ''
    
    function makePassword() {
         
    }
</script>
<style>
    label {
        padding: 10px;
    }
</style>

<h1>Password Maker</h1>

<p>Create a secure password!</p>

<label>
How many charcters do you want your password?<input type="number" bind:value={userLength}>
</label>
<h2>Choose your contents:</h2>
<label>
Letters:<input type="checkbox">
</label>
<lable>
Numbers:<input type="checkbox">
</lable>
<label>
Special Charcters:<input type="checkbox">
</label>

<button on:click={makePassword}>Make Password!</button>

<p>Here is your password:</p>
<p>{password}</p>