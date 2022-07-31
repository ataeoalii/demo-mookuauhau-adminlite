<script lang="ts">
    import { get_person_list } from "$lib/person-access";
    import { jwt_token } from "$lib/nhost";
    import { onMount } from "svelte";

    let personList: Array<any> = [];

	onMount(async() => {
        const data = get_person_list();
        console.log("data: ", data);
        personList = Array.from(data.values());
	});
</script>

{#if personList}
<ul>
    {#each personList as m}
    <li>
        {m.mookuauhau_id}
        {m.filename}
        {m.file_id}
        {m.owner_id}
        {m.load_status}
    </li>
    {/each}
</ul>
{:else}
<div>no m list</div>
{/if}