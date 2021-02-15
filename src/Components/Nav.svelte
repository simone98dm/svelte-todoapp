<script>
  import { onMount } from "svelte";

  import { Link } from "svelte-routing";

  let currentTheme = "light";

  $: currentTheme = localStorage.getItem("theme");

  onMount(() => {
    if (currentTheme === "dark") {
      window.document.body.classList.toggle("dark-mode");
    }
  });

  function onThemeChange() {
    if (currentTheme === "light") {
      currentTheme = "dark";
    } else {
      currentTheme = "light";
    }
    localStorage.setItem("theme", currentTheme);
    window.document.body.classList.toggle("dark-mode");
  }
</script>

<nav class="nav">
  <Link to="/" class="nav-link">Home</Link>
  <Link to="about" class="nav-link">About</Link>
  <span on:click={onThemeChange} class="nav-link">
    {#if currentTheme === "light"}
      <i class="bi bi-brightness-high-fill" />
    {:else}
      <i class="bi bi-moon" />
    {/if}
    &nbsp;Change theme
  </span>
</nav>
