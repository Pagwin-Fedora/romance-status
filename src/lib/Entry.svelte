<script>
import "@picocss/pico/css/pico.min.css";
import { onMount } from 'svelte';
export let item;
function sleep(n){
    return new Promise((res,rej)=>setTimeout(res,n))
}
const table = {
    Complete: "color:green;",
    Failed: "color:red;",
    Pending: "color:#bbb;",
    Ongoing: "color:#36f;"
}
let stdout_contents = "", stderr_contents = "";
onMount(async ()=>{
    while(true){
	try{
	    stdout_contents = await fetch(window.origin + "/" + item[0] + "/stdout.log").then(res=>res.text());
	    stderr_contents = await fetch(window.origin + "/" + item[0] + "/stderr.log").then(res=>res.text());
	}
	catch(e){
	}
	await sleep(50);
    }
});

</script>
<tr>
    <td>
	<details>
	    <summary>{item[0]}</summary>
	    <span class="log">stdout:
	    {stdout_contents}</span>
	    <span class="log">stderr:
	    {stderr_contents}</span>
	</details>
    </td>
    <td style={table[item[1]]}>{item[1]}</td>
</tr>
<style>
    td{
	border: 2px solid white;
	margin: auto;
	border-collapse: collapse;
	text-align: center;
    }
    tr {
	border: 5px solid white;
    }
    .log{
	white-space: pre-line;
    }

</style>
