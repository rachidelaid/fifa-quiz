<script>
  import Plan from './lib/Plan.svelte';
  import Form from './lib/Form.svelte';
  import list from './db.json';

  const index = Math.floor(Math.random() * list.length);
</script>

<main>
  <div class="side">
    <Form names={list.map((t) => t.name)} />
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
</style>
