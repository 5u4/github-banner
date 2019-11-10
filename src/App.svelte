<script>
  import { onMount } from "svelte";

  const CANVAS_WIDTH = 560;
  const CANVAS_HEIGHT = 220;

  let canvasRef;
  let projectName = "Github Banner";
  let fontSize = 32;
  let fontFamily = "'Varela Round'";

  const code = `<p align="center"><img src="./assets/banner.png" /></p>`;

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
    /* outline: #aaa 3px solid; */
    font-family: "Varela Round", sans-serif;
    -moz-box-shadow: 0 0 3px 6px #dddddd94;
    -webkit-box-shadow: 0 0 3px 6px #dddddd94;
    box-shadow: 0 0 3px 6px #dddddd94;
    border-width: 2px;
    border-style: solid;
    border-radius: 8px;
    border-color: #aaa;
  }
  input {
    display: block;
    margin: 30px auto;
    font-size: 16px;
    border-width: 2px;
    border-style: solid;
    border-radius: 8px;
    border-color: #aaa;
    -moz-box-shadow: 0 0 1px 3px #dddddd94;
    -webkit-box-shadow: 0 0 1px 3px #dddddd94;
    box-shadow: 0 0 1px 3px #dddddd94;
    padding: 8px;
    outline: none;
    width: 350px;
  }
  input:hover {
    border-color: #3686ff;
  }
  input:focus {
    border-color: #3686ff;
  }
  pre {
    margin: 30px auto;
    background: #f4f4f4;
    border: 1px solid #ddd;
    border-left: 3px solid #3686ff;
    color: #4d4d4d;
    font-family: monospace;
    font-size: 16px;
    max-width: 530px;
    padding: 10px 20px;
    display: block;
    -moz-box-shadow: 0 0 1px 3px #dddddd94;
    -webkit-box-shadow: 0 0 1px 3px #dddddd94;
    box-shadow: 0 0 1px 3px #dddddd94;
    border-width: 2px;
    border-style: solid;
    border-radius: 8px;
  }
</style>

<canvas bind:this={canvasRef} />
<input
  bind:value={projectName}
  on:keypress={e => e.code === 'Enter' && produce()} />
<pre>
  <code>{code}</code>
</pre>
