<script>
import { fly } from 'svelte/transition';
export let data;
export let currentMenu;
</script>
<style>
ul{
    width:500px;
    height:300px;
    padding:200px 0 0 0;   
    position: absolute;
    left:50%;
    top:50%;
    transform:translate(-50%,-50%);
    background:rgba(0,0,0,1);
}
li{
    list-style:none;
    font-size:30px;
    color:#fff;
    font-family:Arial, Helvetica, sans-serif;
    padding:20px;
    text-align: center;
    border:solid 1px rgba(255,255,255,0);
}
.active{
    border:solid 1px rgba(255,255,255,1);
    background:rgba(255,255,255,.1);
}
</style>


<ul transition:fly="{{ x: -800, duration: 500 }}">
{#each data as menu,index}
    <li class={index === currentMenu ? "active": ""}>
        {menu}
    </li>
{/each}
</ul>
