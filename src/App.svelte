<script>
  import Header from './lib/Header.svelte';
  import Results from './lib/Results.svelte';
  import UserInput from './lib/UserInput.svelte';

  let userInput = $state({
    initialInvestment: 10000,
    annualInvestment: 1200,
    expectedReturn: 6,
    duration: 10,
  });

  let inputIsValid = $derived(
    userInput.initialInvestment > 0 &&
      userInput.annualInvestment >= 0 &&
      userInput.expectedReturn > 0 &&
      userInput.duration >= 1
  );
</script>

<Header />
<UserInput bind:userInput />
{#if inputIsValid}
  <Results {userInput} />
{:else}
  <p class="center">Please enter valid data!</p>
{/if}

<style lang="scss">
  @use './styles/vars';
</style>
