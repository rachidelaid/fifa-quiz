<script>
  import Plan from './lib/Plan.svelte';
  import list from './db.json';

  const index = Math.floor(Math.random() * list.length);
</script>

<main>
  <div class="timer" />
  <Plan team={list[index]} />
</main>

<style>
  main {
    display: flex;
    height: 100vh;
    justify-content: center;
    align-items: center;
    padding: 1rem;
  }

  .timer {
    width: 500px;
  }
</style>
