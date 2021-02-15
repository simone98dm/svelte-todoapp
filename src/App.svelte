<script>
  import { Router, Route } from "svelte-routing";
  import Main from "./Components/Main.svelte";
  import Nav from "./Components/Nav.svelte";
  import About from './Components/About.svelte'

  let url = '/';

</script>

<main class="container">
  <Router {url}>
    <Nav />
    <div>
      <Route path="/"><Main /></Route>
      <Route path="about" component={About} />
    </div>
  </Router>
</main>


<style>
	:global(body) {
		background: #ececec;
		color: #242424;
		transition: background-color 0.3s
	}
	:global(body.dark-mode) {
		background: #242424;
		color: #ececec;
	}
</style>