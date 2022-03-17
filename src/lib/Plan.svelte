<script>
  import bg from '../assets/half.png';
  import { onMount } from 'svelte';
  export let team;

  onMount(() => {
    console.log(team);
    team.players.forEach((player) => {
      const img = document.createElement('img');
      img.title = `(${player.position}) ${player.nation}`;
      img.src = player.flag;
      img.style = `
        width: 70px;
        height: 70px;
        border: 1px solid #000;
        border-radius: 50%;
      `;
      console.log(player.position);
      document.querySelector(`.${player.position}`).append(img);
    });
  });
</script>

<div class="plan">
  <img src={bg} alt="plan bg" />
  <div class="sections">
    <div class="row">
      <div class="LF" />
      <div class="CF ST RS LS" />
      <div class="RF" />
    </div>
    <div class="row">
      <div class="LW" />
      <div class="AM" />
      <div class="RW" />
    </div>
    <div class="row">
      <div class="LM" />
      <div class="AM CAM" />
      <div class="RM" />
    </div>
    <div class="row">
      <div class="LCM" />
      <div class="CM" />
      <div class="RCM" />
    </div>
    <div class="row">
      <div class="LDM" />
      <div class="CDM" />
      <div class="RDM" />
    </div>
    <div class="row">
      <div class="LB LWB" />
      <div class="LCB RCB CB" />
      <div class="RB RWB" />
    </div>
    <div class="row">
      <div class="GK" />
    </div>
  </div>
</div>

<style>
  .plan {
    height: 95%;
    aspect-ratio: 1;
    position: relative;
  }

  .plan img {
    width: 100%;
    height: 100%;
    opacity: 0.7;
  }

  .sections {
    display: grid;
    position: absolute;
    top: 0;
    left: 0;
    z-index: 99;
    grid-template-rows: repeat(7, 1fr);
    width: 100%;
    height: 100%;
  }

  .sections .row {
    height: 100%;
    width: 100%;
    display: flex;
    justify-content: space-between;
  }

  .sections .row div {
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 1rem;
  }
</style>
