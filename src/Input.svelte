<script>
  let value = "";
  let response = [];
  let loading = false;

  const handleInput = event => (value = event.target.value);

  $: {
    if (value.length > 3) {
      loading = true;
      fetch(`https://www.omdbapi.com/?s=${value}&apikey=a552f139`)
        .then(res => res.json())
        .then(result => {
          response = result.Search || [];
          loading = false;
        });
    } else response = [];
  }
</script>

<input placeholder="Search movies..." {value} on:input={handleInput} />

{#if loading}
  <strong>loading...</strong>
{:else if response.length > 0}
  <strong>Tenemos {response.length} películas</strong>
{:else}
  <strong>No tenemos películas</strong>
{/if}
