<script>
    export let progressLen;
</script>

<style>
.progressbar-outer{
    background:#e2e2e2;
    height:15px;
    width:100%;
    border-radius:10px;
    border:solid 1px #b1b1b1;
    overflow:hidden;
}
.progress{
    background:green;
    height:100%;
    transition:all 200ms linear;
}

</style>

<div class="progressbar-outer">
    <div class="progress" style='width:{progressLen}%'></div>
</div>