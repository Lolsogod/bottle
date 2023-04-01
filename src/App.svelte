<script lang="ts">
    import type { ChartData } from 'chart.js';
  import Chart from './Chart.svelte';
  let tasks: String[] = []
	let angle: number = 0
	  const spin = () =>{
      if(dat.labels.length > 1)
		    angle = angle + 2 * 360 + Math.random() * 360
        console.log(dat.labels[Math.floor(angle % 360 / (360 /dat.labels.length))])
	  }

    let dat: ChartData = {
    labels: [],
    datasets: [
      {
        data: [],
        backgroundColor: ["red", "blue", "green", "yellow", "purple", "orange", "violet", "chocolate", "coral", "crimson"],
        borderWidth: 0,
      }
    ]
  };

  let curName: String = ""
  let curTask: String = ""
  const add = () => {
    if(dat.labels.length > 9)
      return
    dat.labels.push(curName)
    dat.datasets[0].data.push(1)
    dat = dat
  }
  const addTask = () => {
    tasks.push(curTask)
  }
</script>

<main>
  <div id="bottle">
    <div class="pointer-wrap"> 
      <div id="chart-wrap"><Chart bind:data={dat}/></div>
      <img style:transform={`rotate(${angle}deg)`} id="pointer" src="/resources/bottle.png" alt="pointer" />
    </div>
    <div class="btn-wrap">
      <button on:click={spin} id="btn" class="btn">Крутить</button>
    </div>
    <div>
      <input type="text" bind:value={curName}><button class="btn" on:click={add}>Добавить игрока</button>
      <input type="text" bind:value={curTask}><button class="btn" on:click={addTask}>Добавить задачу</button>
    </div>
  </div>
    
    
</main>

<style>
	   *{
        margin: 0;
        padding: 0;
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
        width: 40rem;
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
</style>