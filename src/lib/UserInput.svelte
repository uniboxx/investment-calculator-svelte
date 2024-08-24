<script>
  import UserInputField from './UserInputField.svelte';

  let { userInput = $bindable() } = $props();
</script>

<section id="user-input">
  <div class="input-group">
    <UserInputField
      label="Initial Investment"
      bind:value={userInput.initialInvestment} />
    <UserInputField
      label="Annual Investments"
      bind:value={userInput.annualInvestment} />
  </div>
  <div class="input-group">
    <UserInputField
      label="Expected Return"
      bind:value={userInput.expectedReturn} />
    <UserInputField label="Duration" bind:value={userInput.duration} />
  </div>
</section>

<style lang="scss">
  @use '../styles/vars';

  #user-input {
    padding: 1rem;
    max-width: 30rem;
    margin: 2rem auto;
    border-radius: 4px;
    background: linear-gradient(180deg, #307e6c, #2b996d);
  }

  .input-group {
    display: flex;
    justify-content: space-evenly;
    gap: 1.5rem;
  }
</style>
