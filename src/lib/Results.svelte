<script>
  import { calculateInvestmentResults, formatter } from '../util/investment';

  let { userInput } = $props();
  let resultsData = $derived.by(() => calculateInvestmentResults(userInput));

  let totalInterests = $derived.by(() => {
    let totalInterests = [];
    for (let i = 0; i < resultsData.length; i++) {
      let totalInterest = 0;
      for (let j = 0; j <= i; j++) {
        totalInterest += resultsData[j].interest;
      }
      totalInterests.push(totalInterest);
    }
    return totalInterests;
  });

  let totalInvestments = $derived.by(() => {
    let totalInvestments = resultsData.map(
      el => userInput.initialInvestment + userInput.annualInvestment * el.year
    );
    return totalInvestments;
  });
</script>

<table id="result">
  <thead>
    <tr>
      <th>Year</th>
      <th>Investment Value</th>
      <th>Interest (Year)</th>
      <th>Total Interest</th>
      <th>Invested Capital</th>
    </tr>
  </thead>
  <tbody>
    {#each resultsData as yearData, idx (yearData.year)}
      <tr>
        <td>{yearData.year}</td>
        <td>{formatter.format(yearData.valueEndOfYear)}</td>
        <td>{formatter.format(yearData.interest)}</td>
        <td>{formatter.format(totalInterests[idx])}</td>
        <td>{formatter.format(totalInvestments[idx])}</td>
      </tr>
    {/each}
  </tbody>
</table>

<style lang="scss">
  @use '../styles/vars';

  #result {
    max-width: 50rem;
    margin: 2rem auto;
    padding: 1rem;
    table-layout: fixed;
    border-spacing: 1rem;
    text-align: right;
  }

  #result thead {
    font-size: 0.7rem;
    color: #83e6c0;
  }

  #result tbody {
    font-family: 'Roboto Condensed', sans-serif;
    font-size: 0.85rem;
    color: #c2e9e0;
  }
</style>
