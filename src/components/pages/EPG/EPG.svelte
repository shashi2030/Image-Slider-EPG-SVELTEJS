<script>
  import EpgProgram from "../../templates/EpgProgram/EpgProgram";
  import EpgChannel from "../../templates/EpgChannel/EpgChannel";
  import { screen } from "../../../store.js";
  import Data from "./data.json";
  import { fade } from "svelte/transition";

  /* keyeventhandlar */
  function handleKeydown(event) {
    let keyCode = event.keyCode;
    switch (keyCode) {
      case 39:
        rightSlider();
        break;
      case 37:
        leftSlider();
        break;
      case 40:
        downSlider();
        break;
      case 38:
        upSlider();
        break;
      default:
        break;
    }
  }

  /*slider function */
  let currentRow = 0;
  let currentCol = 0;
  let totalProgram = 15;
  let totalChannel = Data.channels.length - 1;
  let progWidth = 300;
  let channelHeight = 78;
  let xPos = 0;
  let yPos = 0;
  var rightSlider = () => {
    if (currentCol < totalProgram) {
      currentCol += 1;
      xPos = -(currentCol * progWidth);
    }
  };

  var leftSlider = () => {
    if (currentCol == 0) {
      screen.update(() => "menu");
    }
    if (currentCol > 0) {
      currentCol -= 1;
      xPos = -(currentCol * progWidth);
    }
  };

  var upSlider = () => {
    if (currentRow > 0) {
      currentRow -= 1;
      yPos = -(currentRow * channelHeight);
    }
  };

  var downSlider = () => {
    if (currentRow < totalChannel) {
      currentRow += 1;
      yPos = -(currentRow * channelHeight);
    }
  };
</script>

<style>
  .wrapper {
    display: flex;
    width: 1200px;
    height: 469px;
    margin: 90px auto 0 auto;
  }
  .programWrapper {
    width: 900px;
    height: 469px;
    overflow: hidden;
    position: relative;
  }
  .channelList {
    width: 300px;
    position: relative;
    box-sizing: border-box;
    overflow: hidden;
    background: rgba(255, 255, 255, 0.3);
  }
</style>

<div class="wrapper" transition:fade>
  <div class="channelList">
    <EpgChannel channelList={Data.channels} {currentRow} {yPos} />
  </div>
  <div class="programWrapper">
    <EpgProgram {progWidth} {xPos} {yPos} {currentRow} {currentCol} channelList={Data.channels} />
  </div>
</div>
<svelte:window on:keydown={handleKeydown} />
