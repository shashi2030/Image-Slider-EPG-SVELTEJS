<script>
    import Slider from '../../organisms/slider/slider.svelte';
    import Paging from './paging.svelte';
    export let sliderData;
    export let animPos;
    export let currentSlide;
</script>

<style>
    .slider-container{
        position:relative;
        left:0px;
        top:50px;
        overflow:hidden;
        height:400px;
        width:1200px;
    }
</style>

<div class="slider-container">
	<Slider sliderData={sliderData} animPos={animPos} />
</div>

<Paging sliderData={sliderData} currentSlide={currentSlide} />