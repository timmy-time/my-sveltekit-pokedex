<script>
    import {pokemon} from "../stores/pokestore"
    import PokemanCard from "../components/pokemanCard.svelte";

    let searchTerm = "";
    let filteredPokeman = [];

    $: {
        if(searchTerm) {
            filteredPokeman = $pokemon.filter(pokeman => pokeman.name.toLowerCase().includes(searchTerm.toLowerCase()))
        } else {
            filteredPokeman = [...$pokemon]
        }
    }
</script>
<svelte:head>
    <title>Svelte Kit Pokedex</title>
</svelte:head>
<h1 class="text-4xl text-center my-8 uppercase">Svelte Kit Podadex</h1>

<input class="w-full rounded-md text-lg p-4 border-2 border-gray-200" type="text" bind:value={searchTerm} placeholder="Search Pokemon">

<div class="py-4 grid gap-4 md:grid-cols-2 grid-cols-1">
{#each filteredPokeman as pokeman}
    <PokemanCard pokeman={pokeman}/>
{/each}
</div>