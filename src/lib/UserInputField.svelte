<script>
  let { label, value = $bindable() } = $props();
  const id = label.toLowerCase().split(' ').join('-');
</script>

<p>
  <label for={id}>{label}</label>
  <input {id} type="number" required bind:value />
</p>

<style lang="scss">
  @use '../styles/vars';

  label {
    display: block;
    margin-bottom: 0.25rem;
    font-family: 'Roboto Condensed', sans-serif;
    font-size: 0.5rem;
    font-weight: bold;
    text-transform: uppercase;
  }

  input {
    width: 100%;
    padding: 0.5rem;
    border: 1px solid #76c0ae;
    border-radius: 0.25rem;
    background-color: transparent;
    color: #c2e9e0;
    font-size: 1rem;
  }
</style>
