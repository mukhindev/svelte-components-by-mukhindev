<script>
import InputMoveControl from './components/InputMoveControl.svelte'

let valueInput = 120
</script>

<style>
.wrap {
  height: 100vh;
  width: 100vw;
}

.center {
  margin: auto;
}

.unselectable {
  user-select: none;
}

</style>

<div class="wrap d-flex align-items-center">
  <div class="center col-2">
    <InputMoveControl bind:value={valueInput}/>
    <p class="mt-3 unselectable">Результат из компонента: {valueInput}</p>
  </div>
</div>
