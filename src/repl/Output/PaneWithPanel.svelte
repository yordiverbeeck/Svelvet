<script>
  import { spring } from 'svelte/motion';
  import SplitPane from '../SplitPane.svelte';

  export let panel;
  export let pos = 50;
  let previous_pos = Math.min(pos, 70);

  let max;

  // we can't bind to the spring itself, but we
  // can still use the spring to drive `pos`
  const driver = spring(pos);
  $: pos = $driver;

  const handleNewNode = (e) => {
    // Creating a default new node template
    let newUserNode = {
      id: initialNodes.length + 1,
      position: { x: 300, y: 25 },
      data: { label: 'New User Created Node' },
      width: 175,
      height: 40,
      bgColor: '#FFB8B8',
      borderColor: 'transparent'
    };
    // Add newly created node on click to initalNodes array to render
    initialNodes.push(newUserNode);
    //reassign initialNodes to tell compiler to rewrite the array holding the nodes
    initialNodes = initialNodes;
  };

  const toggle = () => {
    driver.set(pos, { hard: true });

    if (pos > 80) {
      driver.set(previous_pos);
    } else {
      previous_pos = pos;
      driver.set(max);
    }
  };
</script>

<SplitPane bind:max type="vertical" bind:pos>
  <section slot="a">
    <slot name="main" />
  </section>

  <section class="panel-b" slot="b">
    <div class="panel-header" on:click={toggle}>
      <h3>{panel}</h3>
      <slot name="panel-header" />
    </div>

    <div class="panel-body">
      <slot name="panel-body" />
    </div>
  </section>
</SplitPane>

<style>
  .panel-header {
    height: 42px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 0.5em;
    cursor: pointer;
    border-top: solid 1px;
    /* border-top-color: black; */
  }

  .slot-a {
    border-right: 1px;
  }

  .panel-body {
    overflow: auto;
  }

  /* .panel-b {
		border: 5px;
		border-top-color: black;
	} */

  h3 {
    font: 700 12px/1.5 var(--font);
    color: #333;
  }

  section {
    overflow: hidden;
  }
</style>
