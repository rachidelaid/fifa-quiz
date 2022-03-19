<script>
  import { createEventDispatcher } from 'svelte';
  export let names;

  const dispatch = createEventDispatcher();

  let choose = false;
  let term = '';

  const chooseTeam = (e) => {
    choose = true;
    term = e.target.textContent;
  };

  const reset = () => {
    if (!term.trim()) {
      choose = false;
    }
  };

  const submit = (e) => {
    e.preventDefault();

    if (choose) {
      dispatch('answer', {
        term,
      });

      choose = false;
      term = '';
    }
  };
</script>

<form on:submit={(e) => submit(e)}>
  {#if term && !choose}
    <div class="options">
      {#each names.filter((t) => t
          .toLowerCase()
          .includes(term.trim().toLowerCase())) as team}
        <p on:click={(e) => chooseTeam(e)}>{team}</p>
      {/each}
    </div>
  {/if}
  <input
    type="text"
    placeholder="Team Name"
    bind:value={term}
    on:input={reset}
  />
  <button>Lock Answer</button>
</form>

<style>
  form {
    width: 100%;
    display: flex;
    flex-direction: column;
    gap: 1rem;
    padding: 1rem;
    position: relative;
  }

  input {
    width: 100%;
    padding: 0.4rem;
    outline: none;
    border-radius: 0.4rem;
    background-color: transparent;
    color: white;
  }

  button:hover {
    color: limegreen;
  }

  .options {
    position: absolute;
    max-height: 200px;
    overflow: auto;
    width: 95%;
    bottom: 100px;
    padding: 0.4rem 0;
  }

  .options p {
    padding: 0.4rem 0.2rem;
    background-color: #999;
    border-radius: 0.4rem;
    cursor: pointer;
  }

  .options p:not(:last-child) {
    margin-bottom: 0.3rem;
  }

  .options p:hover {
    background-color: #ddd;
  }
</style>
