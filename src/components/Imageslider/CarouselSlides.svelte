<script>
  import { slideIndex } from "../../utilities/stores";
  import { fade } from "svelte/transition";

  /* Media to bundle */
  import img1 from "../../media/img_lights_wide.jpg";
  import img2 from "../../media/img_mountains_wide.jpg";
  import img3 from "../../media/img_nature_wide.jpg";

  let images = [
    {
      id: 0,
      src: img1,
      caption: "First title",
      color: "text-light"
    },
    {
      id: 1,
      src: img2,
      caption: "Second Title",
      color: "text-light"
    },
    {
      id: 2,
      src: img3,
      caption: "Third Title",
      color: "text-light"
    }
  ];

  /** with this 'reactive declaration' we can handle change of the store's value
   * and draw a respective slider
   * */
  $: itemtoDraw = images[$slideIndex];
</script>

<style>
  .carousel {
    background: no-repeat center center scroll;
    background-size: cover;
    height: 250px;
  }

  @media (max-width: 500px) {
    .carousel {
      height: 200px;
    }
    .carousel__caption {
      width: 65%;
    }
  }

  .carousel__caption--transparent {
    opacity: 0.8;
  }
</style>

<div class="carousel-inner">

  {#each images as { id, src, caption, color }}
    <!-- one of the ways we can render only one slider to the DOM instead of three -->
    {#if $slideIndex === id}
    <!-- Slider with picture inside -->
      <div
        class:active={id === $slideIndex}
        class="carousel carousel-item d-flex flex-column justify-content-center
        align-items-center"
        style="background-image: url({src});"
        transition:fade>
        <!-- Slider's caption -->
        <section
          class="carousel__caption carousel__caption--transparent {color}
          bg-dark px-2 mx-auto my-5">
          <h2>{caption}</h2>
          <p class="h5">This is a paragraph for the {caption}.</p>
        </section>
      </div>
    {/if}
  {/each}
</div>
