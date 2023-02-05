<script>
    import Table from './lib/Table.svelte';
    import { onMount } from 'svelte';
    let data = [];
    function sleep(n){
	return new Promise((res,rej)=>setTimeout(res,n))
    }
    var headers = new Headers();
    headers.append('pragma', 'no-cache');
    headers.append('cache-control', 'no-cache');
    onMount(async ()=>{
	while(true){
	    try{
		data = await fetch(window.origin + "/status.json",{headers}).then(res=>res.json());
	    }
	    catch(e){}
	    await sleep(50);
	}
    });
</script>

<main>
    <div id="center">
    <Table content={data}></Table>
    </div>
</main>
<style>
div{
    display: block;
    margin: auto;
    width:50%;
}

</style>
