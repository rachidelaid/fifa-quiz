<script>
  import Plan from './lib/Plan.svelte';
</script>

<main>
  <div class="timer" />
  <Plan />
</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    background-color: #111;
  }

  *,
  *::after,
  *::before {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }

  main {
    display: flex;
    height: 97vh;
    justify-content: center;
    align-items: center;
  }

  .timer {
    width: 500px;
  }
</style>
