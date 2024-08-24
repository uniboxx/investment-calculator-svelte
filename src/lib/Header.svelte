<script>
  import logo from '../assets/investment-calculator-logo.png';
</script>

<header id="header">
  <img src={logo} alt="Logo showing a money bag" />
  <h1>Investment Calculator</h1>
</header>

<style lang="scss">
  @use '../styles/vars';

  #header {
    text-align: center;
    margin: 3rem auto;
  }

  #header img {
    width: 5rem;
    height: 5rem;
    object-fit: contain;
    background-color: transparent;
  }

  #header h1 {
    font-size: 1.5rem;
  }
</style>
