<script lang="ts">

    import Form from "$lib/Form/Form.svelte";
    import Footer from "$lib/Footer/Footer.svelte";
    import type { ITodos } from '$lib/Models/models';
    import { todosStore } from "../store/store";
    import { page } from '$app/stores';
    
    // Get the data from load function from +layout.ts
    export let data: any;
    
    // Set it in the correct format in the store
    todosStore.set(Object.keys(data).map( (key:any) => { return data[key]; }) as ITodos[]);

</script>


<!--Here are the Navbar, Header and Todo list -->
<section>
    <slot />
</section>

<!--When the page is "not existing page" do not apply the layout-->
{#if $page.url.pathname === "/" || $page.url.pathname ==="/active" || $page.url.pathname === "/done"}
<!--Form for adding new todo-->
<Form />

<!--Fotter with input for name-->
<Footer />
{/if}