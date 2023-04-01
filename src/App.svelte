<script lang="ts">
    import type { ChartData } from 'chart.js';
  import Chart from './Chart.svelte';
	let angle: number = 0
	  const spin = () =>{
		  angle = angle + 2 * 360 + Math.random() * 360
	  }

    let dat: ChartData = {
    labels: [],
    datasets: [
      {
        data: [],
        backgroundColor: ["red", "blue", "green", "blue", "red", "blue"],
        hoverBackgroundColor: []
      }
    ]
  };

  let curName: String = ""
  const add = () => {
    dat.labels.push(curName)
    dat.datasets[0].data.push(1)
    dat = dat
  }
</script>

<main>
	<h1 class="title">Идите нахуй</h1>
  <div id="bottle">
    <div class="pointer-wrap"> 
      <div id="chart-wrap"><Chart bind:data={dat}/></div>
      <img style:transform={`rotate(${angle}deg)`} id="pointer" src="https://svyatoyistochnik.com/local/templates/main/img/bottles/1.png" alt="pointer" />
    </div>
    <div class="btn-wrap">
      <button on:click={spin} id="btn" class="btn">Run</button>
    </div>
    <div>
      <input type="text" bind:value={curName}><button class="btn" on:click={add}>+</button>
    </div>
  </div>
    
    
</main>

<style>
	   *{
        margin: 0;
        padding: 0;
      }
      .title {
        margin: 20px;
        text-align: center;
      }
      .pointer-wrap {
        height: 50rem;
        display: flex;
        position: relative;
        width: 100%;
        justify-content: center;
        align-items: center;
        margin: 20px 0;
      }
      #chart-wrap{
        width: 50rem;
        position: absolute;
      }
      #pointer {
        position: absolute;
        height: 400px;
        transition: transform 3000ms ease-in-out;
      }
      .btn-wrap {
        text-align: center;
      }
      #bottle{
        display: flex;
        flex-direction: column;
      }
	  .btn {
		background-color: #af4c4c; /* Green */
		border: none;
		color: white;
		padding: 15px 32px;
		text-align: center;
		text-decoration: none;
		display: inline-block;
		font-size: 16px;
	 }
   h1{
    color: yellow;
   }
</style>