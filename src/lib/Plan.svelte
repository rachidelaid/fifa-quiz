<script>
  import bg from '../assets/half.png';
</script>

<div class="plan">
  <img src={bg} alt="plan bg" />
  <div class="sections">
    <div class="row">
      <div class="CF" />
    </div>
    <div class="row">
      <div class="LW" />
      <div class="AM" />
      <div class="RW" />
    </div>
    <div class="row">
      <div class="LM" />
      <div class="AM" />
      <div class="RM" />
    </div>
    <div class="row">
      <div class="LCM" />
      <div class="CM" />
      <div class="RCM" />
    </div>
    <div class="row">
      <div class="CDM" />
    </div>
    <div class="row">
      <div class="LWB" />
      <div class="LB" />
      <div class="LCB" />
      <div class="RCB" />
      <div class="RB" />
      <div class="RWB" />
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
    gap: 2px;
  }

  .sections .row {
    background-color: rgba(255, 0, 0, 0.7);
    height: 100%;
    width: 100%;
    display: flex;
    justify-content: space-between;
  }

  .sections .row div {
    border: 2px solid #000;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>
