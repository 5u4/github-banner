<script>
  import { onMount } from "svelte";

  const CANVAS_WIDTH = 560;
  const CANVAS_HEIGHT = 220;

  let canvasRef;
  let projectName = "Github Banner";
  let fontSize = 32;
  let fontFamily = "'Varela Round'";

  const produce = () => {
    const ctx = canvasRef.getContext("2d");
    ctx.clearRect(0, 0, CANVAS_WIDTH, CANVAS_HEIGHT);
    ctx.font = `${fontSize}px ${fontFamily}`;
    ctx.textAlign = "center";
    ctx.textBaseline = "middle";
    ctx.fillStyle = "#000";
    ctx.fillText(projectName, CANVAS_WIDTH / 2, CANVAS_HEIGHT / 2);
  };

  onMount(() => {
    canvasRef.width = CANVAS_WIDTH;
    canvasRef.height = CANVAS_HEIGHT;
    produce();
  });
</script>

<style>
  canvas {
    margin: 30px auto;
    display: block;
    outline: #aaa 3px solid;
    font-family: "Varela Round", sans-serif;
  }
  input {
    margin: 30px auto;
    display: block;
  }
</style>

<canvas bind:this={canvasRef} />
<input
  bind:value={projectName}
  on:keypress={e => e.code === 'Enter' && produce()} />
