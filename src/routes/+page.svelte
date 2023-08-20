<script lang="ts">
  import { onMount } from "svelte";
  import "../styles.css";
  import { sideOfBall } from "$lib/ballsStore";
  const data = {
    "P&10": {
      runtab: {
        personel: {
          "0": "OVR",
          "1": "24",
          "2": "15",
          "3": "33",
        },
        "run%": {
          "0": "Run%",
          "1": "Run%",
          "2": "Run%",
          "3": "Run%",
        },
        "Run/Pass": {
          "0": "42%",
          "1": "3%",
          "2": "10%",
          "3": "15%",
        },
        "Type/ Zone thrown/ Concept": {
          "0": "Run St%",
          "1": "Run St%",
          "2": "Run St%",
          "3": "Run St%",
        },
        Direction: {
          "0": "4%",
          "1": "56%",
          "2": "77%",
          "3": "100%",
        },
      },
      last5Plays: {
        down: {
          "0": "p",
          "1": "1",
          "2": "1",
          "3": "1",
          "4": "p",
        },
        dist: {
          "0": "10",
          "1": "10",
          "2": "5",
          "3": "20",
          "4": "10",
        },
        Personnel: {
          "0": "33",
          "1": "24",
          "2": "24",
          "3": "24",
          "4": "24",
        },
        "Run/Pass": {
          "0": "Pass",
          "1": "Run",
          "2": "Pass",
          "3": "Run",
          "4": "Run",
        },
        "Type/ Zone thrown/ Concept": {
          "0": "Z do",
          "1": "counter trey",
          "2": "double out",
          "3": "ct trey",
          "4": "t power",
        },
        Direction: {
          "0": "Strong",
          "1": "Strong",
          "2": "Strong",
          "3": "Strong",
          "4": "Strong",
        },
        "GN/LS": {
          "0": "23",
          "1": "3",
          "2": "18",
          "3": "-10",
          "4": "-10",
        },
      },
      bestPlays: {
        down: {
          "0": "p",
          "1": "1",
        },
        dist: {
          "0": "10",
          "1": "10",
        },
        Personnel: {
          "0": "33",
          "1": "24",
        },
        "Run/Pass": {
          "0": "Pass",
          "1": "Run",
        },
        "Type/ Zone thrown/ Concept": {
          "0": "Z do",
          "1": "counter trey",
        },
        Direction: {
          "0": "Strong",
          "1": "Strong",
        },
        "GN/LS": {
          "0": "-17",
          "1": "-5",
        },
      },
    },
    "1&10": {
      runtab: {
        personel: {
          "0": "OVR",
          "1": "24",
          "2": "15",
          "3": "33",
        },
        "run%": {
          "0": "Run%",
          "1": "Run%",
          "2": "Run%",
          "3": "Run%",
        },
        "Run/Pass": {
          "0": "42%",
          "1": "3%",
          "2": "10%",
          "3": "15%",
        },
        "Type/ Zone thrown/ Concept": {
          "0": "Run St%",
          "1": "Run St%",
          "2": "Run St%",
          "3": "Run St%",
        },
        Direction: {
          "0": "4%",
          "1": "56%",
          "2": "77%",
          "3": "100%",
        },
      },
      last5Plays: {
        down: {
          "0": "p",
          "1": "1",
          "2": "1",
          "3": "1",
          "4": "p",
        },
        dist: {
          "0": "10",
          "1": "10",
          "2": "5",
          "3": "20",
          "4": "10",
        },
        Personnel: {
          "0": "33",
          "1": "24",
          "2": "24",
          "3": "24",
          "4": "24",
        },
        "Run/Pass": {
          "0": "Pass",
          "1": "Run",
          "2": "Pass",
          "3": "Run",
          "4": "Run",
        },
        "Type/ Zone thrown/ Concept": {
          "0": "Z do",
          "1": "counter trey",
          "2": "double out",
          "3": "ct trey",
          "4": "t power",
        },
        Direction: {
          "0": "Strong",
          "1": "Strong",
          "2": "Strong",
          "3": "Strong",
          "4": "Strong",
        },
        "GN/LS": {
          "0": "23",
          "1": "3",
          "2": "18",
          "3": "-10",
          "4": "-10",
        },
      },
      bestPlays: {
        down: {
          "0": "p",
          "1": "1",
        },
        dist: {
          "0": "10",
          "1": "10",
        },
        Personnel: {
          "0": "33",
          "1": "24",
        },
        "Run/Pass": {
          "0": "Pass",
          "1": "Run",
        },
        "Type/ Zone thrown/ Concept": {
          "0": "Z do",
          "1": "counter trey",
        },
        Direction: {
          "0": "Strong",
          "1": "Strong",
        },
        "GN/LS": {
          "0": "-17",
          "1": "-5",
        },
      },
    },
  };

  // let currentSituation = ''

  // function setSituation(situation:string){
  //     currentSituation = situation
  // }

  // $: if(currentSituation !== '') {

  // }

  // let currentOption = '';

  // function setOption(option: string) {
  //     currentOption = option;
  // }
  let currentKey = Object.keys(data)[0]; // Default to first key
  let currentSubKey = Object.keys(data[currentKey])[0]; // Default to first sub-key
  let currentSubData = data[currentKey][currentSubKey];

  function setKey(key) {
    currentKey = key;
    currentSubKey = Object.keys(data[currentKey])[0]; // Reset subKey when changing main key
    currentSubData = data[currentKey][currentSubKey];
  }

  function setSubKey(subKey) {
    currentSubKey = subKey;
    currentSubData = data[currentKey][currentSubKey];
  }
</script>

<main>
  <!-- Navigation Buttons -->
  <div class="situations">
    {#each Object.keys(data) as key}
      <button
        on:click={() => setKey(key)}
        class={currentKey === key ? "selected" : ""}>{key}</button
      >
    {/each}
  </div>

  <!-- Sub-Navigation Buttons -->
  <div class="subSituations">
    {#each Object.keys(data[currentKey]) as subKey}
      <button
        on:click={() => setSubKey(subKey)}
        class={currentSubKey === subKey ? "selected" : ""}>{subKey}</button
      >
    {/each}
  </div>

  <!-- Displaying Data -->
  <table>
    <thead>
      <tr>
        {#each Object.keys(currentSubData) as columnKey}
          <th>{columnKey}</th>
        {/each}
      </tr>
    </thead>
    <tbody>
      {#each Object.keys(currentSubData[Object.keys(currentSubData)[0]]) as rowIndex}
        <tr>
          {#each Object.keys(currentSubData) as columnKey}
            <td>{currentSubData[columnKey][rowIndex]}</td>
          {/each}
        </tr>
      {/each}
    </tbody>
  </table>
</main>

<style>
  .situations {
    display: flex;
    gap: 1rem;
    width: 100%;
    justify-content: center;
  }

  .subSituations {
    display: flex;
    gap: 1rem;
    width: 100%;
    justify-content: center;
  }
  main {
    display: flex;
    flex-direction: column;
    flex: 1 auto;
    width: 100%;
    gap: 2rem;
  }

  .upload {
    width: 100%;
    border: 1px solid black;
    padding: 1rem;
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }

  form {
    display: flex;
    flex-direction: column;
    gap: 2rem;
  }

  label {
    display: flex;
    gap: 1rem;
    font-size: 1.5rem;
  }

  button {
    width: max-content;
    background-color: var(--primary);
    padding: 0.5rem 1rem;
    border-radius: 1rem;
    font-size: 1.5rem;
  }

  h2 {
    font-size: 2rem;
  }

  input {
    font-size: 1.5rem;
  }
  .selected {
    background-color: grey; /* Choose your own secondary color, or define any color here */
    color: white;
    border: 1px solid white;
  }

  table{
    padding: 1rem 2rem;
  }
</style>
