<script>
import Thumbnaillist from '../../molecules/thumbnaillist/thumbnaillist.svelte'; 
export let sliderData;
export let animPos;

const baseUrl = './images/';
</script>

<style>
ul{
	padding:0;
	display:flex;
	position:absolute;
	left:0;
	top:0;
	transition:all 250ms ease-in-out;
}

</style>


	<ul style="transform: translate3d({animPos}px,0,0)">
		{#each sliderData as slide}
			<Thumbnaillist baseUrl={baseUrl} items={slide} />
		{/each}
	</ul>
