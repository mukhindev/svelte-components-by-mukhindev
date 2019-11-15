<script>
export let value

let control = 0
let offset = 0
let last = value
let active = ''

function down () {
  control = 1
  last = value
  offset = event.y
  if (offset !== 0) {
    value = last + -event.y + offset
  } else {
    value = last + -event.y
  }
  active = 'active'
  onmousemove = move
}

function move () {
  if (control === 1) {
    if (offset !== 0) {
      value = last + -event.y + offset
    } else {
      value = last + -event.y
    }
    onmouseup = up
    document.body.style.cursor = "ns-resize";
  }
}

function up () {
  if (control === 1) { 
    if (offset !== 0) {
      value = last + -event.y + offset
    } else {
      value = last + -event.y
    }
    last = value
  }
  control = 0
  active = ''
  document.body.style.cursor = "default";
}
</script>

<style>
.position1 {
  position: absolute;
  top: 50%;
  width: 12px;
  height: 34px;
  right: 0;
}
.position2 {
  position: absolute;
  background-color: rgb(255, 255, 255);
  top: -50%;
  width: 20px;
  height: 34px;
  right: 8px;
}
.position2:before {
  content: '';
  position: absolute;
  width: inherit;
  height: 38px;
  top: -1px;
  cursor: ns-resize;
}
.marker {
  right: -8px;
  position: absolute;
  width: 34px;
  height: 34px;
  border-radius: 100%;
  background-color: #C4DFFE;
  transition: 0.25s;
  transform: scale(0.25);
  cursor: ns-resize;
}
.marker.active {
  transform: scale(0.5);
  transition: 0.25s;
}
.relative {
  position: relative;
}
.unselectable {
  user-select: none;
}
</style>

<div class="relative">
  <input type="number" bind:value={value} value="{value}" class="form-control">
  <div class="position1">
    <div on:mousedown={down} class="position2">
      <div class="marker unselectable {active}">
      </div>
    </div>
  </div>
</div>
