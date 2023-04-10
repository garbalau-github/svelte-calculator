<script lang="ts">
  const numbers = ['1', '2', '3', '4', '5', '6', '7', '8', '9', '0', '.'];
  const operations = ['/', 'x', '+', '-', '='];

  // States
  let selectedOperation = '';
  let display = '';

  // Handlers
  const handleOperationClick = (operation: string) => {
    selectedOperation = operation;
  };

  const handleNumberClick = (number: string) => {
    // Basic Validation
    if (display === '' && number === '0') return;
    if (number === '.' && display.includes('.')) return;
    display += number;
  }

</script>

<main>
  <div class='calculator'>
    <div class='results'>
      {display}
    </div>
    <div class='digits'>
      <div class='numbers'>
        <button class="btn btn-xlg btn-silver">C</button>
        {#each numbers as number (number)}
          <button 
            on:click={() => handleNumberClick(number)}  
            class={`btn ${number === '0' ? 'btn-lg' : null}`}>
            {number}
          </button>
        {/each}
      </div>
      <div class='operations'>
        {#each operations as operation (operation)}
          <button 
            on:click={() => handleOperationClick(operation)}
            class={`btn ${operation === selectedOperation ? 'btn-silver' : 'btn-orange'}`} >
            {operation}
          </button>
        {/each}
    </div>
  </div>
</main>


<style>
  main {
    width: 100vw;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .calculator {
    background-color: rgb(28, 28, 28);
    width: 240px;
    padding: 15px;
    border-radius: 7px;
  }
  .results {
    height: 60px;
    color: white;
    font-size: 50px;
    display: flex;
    flex-direction: row-reverse;
    background-color: dimgray;
    margin-bottom: 20px;
    border-radius: 10px;
    padding: 10px;
  }
  .digits {
    display: flex;
  }
  .numbers {
    display: flex;
    flex-wrap: wrap;
    width: 200px;
  }
  .operations {
    display: flex;
    flex-direction: column;
  }
  .btn {
    width: 50px;
    height: 50px;
    border-radius: 100px;
    background-color: rgb(114, 113, 113);
    font-size: 20px;
    font-weight: bold;
    color: white;
    margin: 5px;
    border: none;
    cursor: pointer;
  }
  .btn-lg {
    width: 110px;
  }
  .btn-xlg {
    width: 170px;
  }
  .btn-orange {
    background-color: orange;
  }
  .btn-silver {
    background-color: silver;
  }
</style>
