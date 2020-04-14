<script>
  export let channelList;
  export let currentRow;
  export let yPos;
</script>

<style>
  .channelWrapper {
    margin: 0;
    padding: 0;
    position: absolute;
    left: 0;
    top: 0;
    transition: transform 300ms linear;
    width: 100%;
  }
  .channelName {
    list-style: none;
    font-family: "Arial", "Verdana";
    color: #fff;
    padding: 20px 10px;
    box-sizing: border-box;
    border: solid 1px #fff;
    height: 78px;
    text-align: center;
    font-size: 30px;
  }
</style>

<ul class="channelWrapper" style={`transform:translate3d(0,${yPos}px,0)`}>
  {#each channelList as channel, index}
    <li class={index === currentRow ? 'channelName activeChannel' : 'channelName'}>
      {channel.channelName} </li>
  {/each}
</ul>
