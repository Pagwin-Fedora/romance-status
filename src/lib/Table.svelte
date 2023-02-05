<script>
import "@picocss/pico/css/pico.min.css";
import Entry from "./Entry.svelte";
export let content;
</script>
<table role="grid" style="display: inline-table">
    <thead>
	<tr>
	    <th>Job Name</th>
	    <th>Job Status</th>
	</tr>
    </thead>
    <tbody>
	{#each content as item}
	<Entry item={item}/>
	{/each}
    </tbody>
</table>
<style>
    table {
	border: 5px solid white;
    }
    th{
	border: 2px solid white;
	text-align: center;
    }
    tr {
	border: 5px solid white;
    }
</style>
