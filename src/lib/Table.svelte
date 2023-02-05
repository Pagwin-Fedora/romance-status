<script>
import "@picocss/pico/css/pico.min.css";
export let content;
const table = {
    Complete: "color:green;",
    Failed: "color:red;",
    Pending: "color:#bbb;",
    Ongoing: "color:#36f;"
}
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
	    <tr>
		<td>{item[0]}</td>
		<td style={table[item[1]]}>{item[1]}</td>
	    </tr>
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
    td{
	border: 2px solid white;
	margin: auto;
	border-collapse: collapse;
	text-align: center;
    }
</style>
