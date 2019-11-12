<script>
export let min
export let max

function down () {
  let e = window.event
  console.log('Нажал:', e.y)
  onmouseup = up
}

function up () {
  let e = window.event
  console.log('Отжал:', e.y)
}
</script>

<style>
.box {
  width: 200px;
  height: 200px;
  background-color: blanchedalmond;
}
</style>

<pre class="box" on:mousedown={down}>
min: {min}
max: {max}
</pre>