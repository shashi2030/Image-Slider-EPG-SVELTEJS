<script>
  import Horizontalslider from "../../templates/horizontalslider/horizontalslider.svelte";
  import { onMount, beforeUpdate, afterUpdate } from "svelte";
  import { screen } from "../../../store.js";
  import Progressbar from "./progressbar.svelte";
  import Data from "./data.json";

  /* keyeventhandlar */
  let key;
  let keyCode;

  function handleKeydown(event) {
    key = event.key;
    keyCode = event.keyCode;
    switch (keyCode) {
      case 39:
        rightSlider();
        break;
      case 37:
        leftSlider();
        break;
      default:
        break;
    }
  }

  /*slider function */
  let itemWidth = 300;
  let totalLength = Data.sliderData.length - 4;
  let currentSlide = 0;
  let animatePos = 0;
  let progressLength = 0;
  function rightSlider() {
    if (currentSlide < totalLength) {
      currentSlide++;
      animatePos -= itemWidth;
      progressbar();
    }
  }
  function leftSlider() {
    if (currentSlide == 0) {
      screen.update(() => "menu");
    }
    if (currentSlide >= 1) {
      currentSlide--;
      animatePos += itemWidth;
      progressbar();
    }
  }
  function progressbar() {
    progressLength = (100 * currentSlide) / totalLength;
  }
</script>

<style>
  .wrapper {
    width: 1200px;
    margin: 0 auto;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
  }
</style>

<div class="wrapper">
  <Horizontalslider sliderData={Data.sliderData} animPos={animatePos} {currentSlide} />
  <Progressbar progressLen={progressLength} />

</div>
<svelte:window on:keydown={handleKeydown} />
