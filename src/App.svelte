<script lang="ts">
  import type { ChartData } from "chart.js";
  import Header from "./Header.svelte";
  import Modal from "./Modal.svelte";
  import Welcome from "./Welcome.svelte";
  let winner;
  let winTaskId;
  let winTask;
  let intro = true
  let state = "hidden";
  let tasks: String[] = [];
  let angle: number = 0;
  let showAddUserModal = false;
  let showAddTaskModal: boolean = false;
  let showTaskModal: boolean = false;
  let disabledSpinner: boolean = false;
  let spinning: boolean = false;
  const delay = (ms) => new Promise((res) => setTimeout(res, ms));
  const spin = async () => {
    state = "hidden";
    if (dat.labels.length > 1) {
      disabledSpinner = true;
      angle = angle + 2 * 360 + Math.random() * 360;
      spinning = true;
      await delay(3000);
      spinning = false;
      // TODO пофиксить точность формулы
      winner =
        dat.labels[Math.floor(((angle + (90 / (dat.labels.length - 1))) % 360) / (360 / dat.labels.length))];
      showTaskModal = true;
      if(tasks.length > 0) {
        winTaskId = Math.floor(Math.random() * tasks.length);
        winTask = tasks[winTaskId];
      }
      else
        winTask = "Выполняет действие";
      state = "show";
      disabledSpinner = false;
    }
  };

  const deleteTask = (index: number) => {
    if(spinning)
      return;
    tasks.splice(index, 1);
    tasks = tasks;
    showTaskModal = false;
  }

  const deletePlayer = (index: number) => {
    if(spinning)
      return;
    dat.labels.splice(index, 1);
    dat.labels = dat.labels;
  }

  const getStyleForCircle = (index: number) => {
    const delta = (Math.PI * 2) / dat.labels.length;
    let angle = delta * index;
    return `bottom: ${300 * Math.cos(angle) + "px"}; left: ${
      300 * Math.sin(angle) + "px"
    }`;
  };

  let dat: ChartData = {
    labels: [],
    datasets: [
      {
        data: [],
        backgroundColor: [
          "red",
          "blue",
          "green",
          "yellow",
          "purple",
          "orange",
          "violet",
          "chocolate",
          "coral",
          "crimson",
        ],
        borderWidth: 0,
      },
    ],
  };

  let curName: string = "";
  let curTask: string = "";
  const add = () => {
    showAddUserModal = false;
    if (dat.labels.length > 9) return;
    dat.labels.push(curName);
    dat.datasets[0].data.push(1);
    dat = dat;
    curName = "";
  };
  const addTask = () => {
    showAddTaskModal = false;
    tasks.push(curTask);
    tasks = tasks;
    curTask = "";
  };
</script>

<main>
  {#if intro}
  <Header />
  <div class="welcome-wrapper" on:click={()=>intro = false}>
    <Welcome />
  </div>
  {/if}
  {#if !intro}
  <div class="wrapper">
    <div class="list-players">
      <button class="btn" on:click={() => (showAddUserModal = true)}
        >Добавить игрока</button
      >
      <div class="list">
        Состав сената:
        {#each dat.labels as name, i (i)}
          <div class="player list-item">
            <div class="center">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 48 48"
                width="24px"
                height="24px"
              >
                <path
                  fill={dat.datasets[0].backgroundColor[i]}
                  d="M15,35c-0.5,0-1-0.2-1.4-0.6c-0.8-0.8-0.8-2,0-2.8l26-26c0.8-0.8,2-0.8,2.8,0c0.8,0.8,0.8,2,0,2.8 l-26,26C16,34.8,15.5,35,15,35z"
                />
                <path
                  fill={dat.datasets[0].backgroundColor[i]}
                  d="M14,35c-0.3,0-0.5-0.1-0.7-0.3c-0.4-0.4-0.4-1,0-1.4l27-27c0.4-0.4,1-0.4,1.4,0s0.4,1,0,1.4l-27,27 C14.5,34.9,14.3,35,14,35z"
                />
                <path
                  fill="#90a4ae"
                  d="M8.3,38.3l1.4,1.4L6.4,43L5,41.6L8.3,38.3z"
                />
                <path
                  fill="#90a4ae"
                  d="M14.5,30.7l2.8,2.8L7.8,43L5,40.2L14.5,30.7z"
                />
                <path
                  fill="#37474f"
                  d="M12.1 33.1l2.8 2.8L7.8 43 5 40.2 12.1 33.1zM18 27.2l-3.9 3.9 2.8 2.8 1.1-1.1V27.2z"
                />
                <path fill="#37474f" d="M11,32l3,3l-2,2l-3-3L11,32z" /></svg
              >
              - {name}</div>
            <button class="btn remove" on:click={() => (deletePlayer(i))}>Х</button>
          </div>
        {/each}
      </div>
    </div>
    <div id="bottle">
      <div class="pointer-wrap">
        <div id="chart-wrapper">
          {#each dat.labels as name, i (i)}
            <div class="player {i}" style={getStyleForCircle(i)}>
              <div class="user-icon">
                <img src="/resources/user-icon.svg" alt="user" />
                <img
                  src="/resources/jedai-sward.svg"
                  alt="sward"
                  class="sward"
                  style="filter: drop-shadow(0px 0px 10px {dat.datasets[0]
                    ?.backgroundColor[i]});"
                />
              </div>
              <span>{name}</span>
            </div>
          {/each}
          <img
            style:transform={`rotate(${angle}deg)`}
            id="pointer"
            src="/resources/bottle.png"
            alt="pointer"
          />
        </div>
      </div>
    </div>
    <div class="list-tasks">
      <button
        class="btn"
        on:click={() => {
          showAddTaskModal = true;
        }}>Добавить задачу</button
      >
      <div class="list">
        Задачи:
        {#each tasks as task, i (i)}
            <div class="list-item">
              <span>{i+1}. {task}</span>     
              <button class="btn remove" on:click={() => (deleteTask(i))}>Х</button
            ></div>
        {/each}
      </div>
    </div>
  </div>

  <div class="btn-wrap">
    <button disabled={disabledSpinner} on:click={spin} id="btn" class="btn costil"
      >Крутить</button
    >
  </div>
  <Modal bind:showModal={showAddUserModal}>
    <input bind:value={curName} />
    <button class="btn" on:click={curName ? add : null}>Добавить</button>
  </Modal>

  <Modal bind:showModal={showAddTaskModal}>
    <input bind:value={curTask} />
    <button class="btn" on:click={curTask ? addTask : null}>Добавить</button>
  </Modal>

  <Modal bind:showModal={showTaskModal}>
    <div>{`${winner} : ${winTask}`}</div>
    <div class="buttons-wrapper">
      <button class="btn" on:click={() => (showTaskModal = false)}>ОК</button>
      {#if tasks.length > 0}
        <button class="btn" on:click={() => (deleteTask(winTaskId))}>Удалить задачу</button>  
      {/if}
      </div>
    
  </Modal>
  {/if}
</main>

<style>
  * {
    margin: 0;
    padding: 0;
  }

  .welcome-wrapper {
    margin-top: 45vh;
    position: relative;
    height: 45vh;
  }

  .wrapper {
    display: flex;
    justify-content: space-evenly;
    margin-top: 40px;
  }

  .settings {
    display: flex;
    flex-direction: column;
  }

  .list {
    margin-top: 10px;
    color: white;
    display: flex;
    flex-direction: column;
    gap: 10px;
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

  #chart-wrapper {
    position: relative;
    width: 160px;
    height: 200px;
  }

  input {
    -webkit-appearance: none;
    outline: none;
    border-radius: 10px;
    height: 45px;
    caret-color: transparent;
    font-size: 20px;
    font-weight: 600;
    padding: 5px;
  }

  #pointer {
    position: absolute;
    top: -115px;
    height: 400px;
    transition: transform 3000ms ease-in-out;
  }

  .btn-wrap {
    text-align: center;
  }

  .list .player {
    display: flex;
    flex-direction: row;
  }

  .user-icon {
    position: relative;
  }

  .sward {
    width: 80px;
    position: absolute;
    right: -20px;
    top: -15px;
    filter: saturate(800%);
  }

  #bottle {
    display: flex;
    flex-direction: column;
    width: 600px;
  }

  .btn {
    background-color: #000;
    border: 2px solid #ff6;
    color: #ff6;
    padding: 15px 32px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
  }

  .btn:hover {
    color: #fff;
    transition: all 0.2s ease;
    cursor: pointer;
  }

  .remove{
    background-color: #000;
    border: 2px solid rgb(255, 102, 102);
    color: rgb(255, 102, 102);
    padding: 5px 10px;
  }
  .list-item{
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .center{
    display: flex;
    align-items: center;
  }
  .buttons-wrapper{
    display: flex;
    justify-content: center;
    gap: 10px;
    margin-top: 10px;
  }
  .costil{
    margin-bottom: 70px;
  }
</style>
