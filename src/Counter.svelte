<script>
  export let name = "";
  export let initialCounter = 0;
  export let maxCounter = 0;

  let contador = initialCounter;

  var handleClick = () => {
    contador++;
  };

  $: isEventOrOdd = contador % 2 === 0 ? "Is Even" : "Is Odd";

  $: {
	  if (contador > maxCounter )
		  contador = 0
  }
</script>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

<main>
  <button on:click={handleClick}>cambiar nombre</button>
  <h1>Hello {name}! {contador}</h1>
  <p>
    {isEventOrOdd}
    <!-- {contador % 2 === 0 ? "Is Even" : "Is Odd"} -->
  </p>
</main>
