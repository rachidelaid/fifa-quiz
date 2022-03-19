<script>
  import Plan from './lib/Plan.svelte';
  import Form from './lib/Form.svelte';
  import list from './db.json';

  $: index = Math.floor(Math.random() * list.length);
  $: score = 0;

  let answer = false;
  let win = false;

  const showDetails = () => {
    document.querySelectorAll('.sections img').forEach((img) => img.remove());

    list[index].players.forEach((player) => {
      const div = document.createElement('div');
      div.className = 'player';

      const img = document.createElement('img');
      img.title = `(${player.position}) ${player.nation}`;
      img.src = player.avatar;
      img.className = 'flag';
      div.append(img);

      const p = document.createElement('p');
      p.textContent = player.name;
      div.append(p);

      document.querySelector(`.${player.position}`).append(div);
    });
  };

  const choose = (e) => {
    answer = true;
    showDetails();

    if (e.detail.term === list[index].name) {
      win = true;
      score = score + 1;
      return;
    }

    win = false;
    score = 0;
  };

  const restart = () => {
    document
      .querySelectorAll('.sections .player')
      .forEach((div) => div.remove());
    answer = win = false;
    index = Math.floor(Math.random() * list.length);
  };
</script>

<main>
  <div class="side">
    <h3 class="score">Score: {score}</h3>
    {#if !answer}
      <Form names={list.map((t) => t.name)} on:answer={choose} />
    {/if}
    {#if answer}
      <div class="answer">
        {#if win}
          <h1 class="green">YOU WON</h1>
        {:else}
          <h1 class="red">YOU LOSE</h1>
        {/if}

        <img src={list[index].image} alt="" />
        <h3>{list[index].name}</h3>

        <button on:click={restart}>next</button>
      </div>
    {/if}
  </div>
  <Plan team={list[index]} />
</main>

<style>
  main {
    display: flex;
    height: 100vh;
    justify-content: center;
    align-items: center;
  }

  .side {
    width: 100%;
  }

  .answer {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    color: white;
    margin-top: 2rem;
    padding: 0 2rem;
  }

  .red {
    color: red;
  }

  .green {
    color: green;
  }

  .answer img {
    margin-top: 3rem;
  }

  .answer button {
    width: fit-content;
    padding: 0.5rem 1rem;
    margin-top: 1rem;
  }

  .score {
    position: absolute;
    top: 1rem;
    left: 1rem;
    text-align: center;
    color: #fff;
  }
</style>
