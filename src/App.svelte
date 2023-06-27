<script>
	import Jogar from "./Jogar.svelte";
	import Sobre from "./Sobre.svelte";
	import { estado } from "./Estado.js";
    import Menu from "./Menu.svelte";
</script>

{#if $estado == "jogar"}
	<Jogar />
{:else if $estado == "menu"}
	<Menu />
{:else if $estado == "sobre"}
	<Sobre />
{/if}
