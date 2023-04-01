<script lang="ts">
  import type { ChartData } from 'chart.js';
  import Chart from './Chart.svelte';
  let winner
  let winTask
  let state = 'hidden'
  let tasks: String[] = []
	let angle: number = 0
  const delay = ms => new Promise(res => setTimeout(res, ms));
	  const spin = async () =>{
      state = "hidden"
      if(dat.labels.length > 1){
        angle = angle + 2 * 360 + Math.random() * 360
        await delay(3000)
        winner = dat.labels[Math.floor(angle % 360 / (360 /dat.labels.length))]
        winTask = tasks[Math.floor(Math.random()*tasks.length)];
        state = 'show'
      }
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
  <div class={state}>{`${winner} : ${winTask}`}</div>
  <div class="list">{#each dat.labels as name, i (i)}
    <ol>
      <li>{name} - <span style:color={dat.datasets[0].backgroundColor[i]}>&#9632;</span></li>
    </ol>
  {/each}
  </div>
    
</main>

<style>
	   *{
        margin: 0;
        padding: 0;
      }
      .list{
        color: white;
      }
      .show {
        transition: opacity 0.2s linear;
        color: white;
        opacity: 1;
      }

      .hidden {
        color: white;
        opacity: 0;
        transition: opacity 0.2s linear;
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
      .box {
        float: left;
        height: 20px;
        width: 20px;
        margin-bottom: 15px;
        border: 1px solid black;
        clear: both;
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