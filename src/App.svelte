<script lang="ts">
  import {onMount} from "svelte";

  onMount(() => {
    const sections = document.querySelectorAll('section');
    sections.forEach((el) => observer.observe(el));

    setInterval(() => {
      updateBackground();
    }, 2500);
  })

  const observer: IntersectionObserver = new IntersectionObserver((entries) => {
    entries.forEach((entry: IntersectionObserverEntry) => entry.isIntersecting ? updateBackground(): '');
  })

  function updateBackground() {
    const container = document.getElementById('content');
    container.style.background = '#' + Math.floor(Math.random()*16777215).toString(16);
  }
</script>

<main id="content" class="main-container">
  <section id="profile">
    <h1>ddd</h1>
  </section>
  <section id="formations">
    formations
  </section>
  <section id="experiences">
    experiences
  </section>
</main>

<style lang="scss">

  #content {
    overflow-y: scroll;
    & > :global(*) {
      width: 100%;
      height: 70vh;
    }
  }
</style>