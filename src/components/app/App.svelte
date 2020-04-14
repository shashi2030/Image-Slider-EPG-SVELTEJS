<script>
  import { Router, Route } from "svero";
  import { screen } from "../../store.js";
  import Home from "../pages/EPG/EPG.svelte";
  import EPG from "../pages/EPG/EPG.svelte";
  import SliderImage from "../pages/slider/sliderimage.svelte";
  import Menu from "../templates/Menu/Menu.svelte";
  import { beforeUpdate } from "svelte";

  const menudata = ["Slider", "EPG"];
  const Screen = { EPG: "EPG", slider: "Slider", menu: "menu" };
  $: ScreenName = $screen;

  let currentMenu = 0;
  function handleKeydown(event) {
    var key = event.key;
    var keyCode = event.keyCode;
    switch (keyCode) {
      case 71:
        //G
        ScreenName = Screen.EPG;
        break;
      case 83:
        //S
        ScreenName = Screen.slider;
        break;
      case 38:
        menu();
        break;
      case 40:
        menu();
        break;
      case 13:
        goToPage();
        break;
      case 77:
        ScreenName = Screen.menu;
        break;
      default:
        break;
    }
  }
  var menu = () => {
    if (currentMenu > 0) {
      currentMenu -= 1;
    } else if (currentMenu < menudata.length - 1) {
      currentMenu += 1;
    }
  };

  var goToPage = () => {
    if (currentMenu == 0) {
      ScreenName = Screen.slider;
    } else {
      ScreenName = Screen.EPG;
    }
    screen.update(() => ScreenName);
  };
</script>

{#if ScreenName === Screen.EPG}
  <EPG />
{:else if ScreenName === Screen.slider}
  <SliderImage />
{:else}
  <Menu data={menudata} {currentMenu} />
{/if}
<svelte:window on:keydown={handleKeydown} />
