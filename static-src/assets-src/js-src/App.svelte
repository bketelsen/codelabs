<!-- App.svelte -->
<script>
  import { onMount } from 'svelte';
  import { Router, Link, Route, links } from "svelte-routing";

  import  Courses from "./views/Courses.svelte";
  import  Tutorials from "./views/Tutorials.svelte";
  import  Snacks from "./views/Snacks.svelte";
  import  Snack from "./views/Snack.svelte";
  import  About  from "./views/About.svelte";
  import  Home  from "./views/Home.svelte";
  import { getSitedata } from "./stores/data";
  import  Banner from "./components/Banner.svelte";
  export let url = "";
  export let title = "";


  onMount(() => {
    getSitedata();
  });

</script>
<div use:links>
<Router url="{url}">
  <Banner {title} />
  <main>

    <Route path="tutorials" component="{Tutorials}" />
    <Route path="courses" component="{Courses}" />
    <Route path="snacks/:snackname/" component="{Snack}" />
    <Route path="snacks" component="{Snacks}" />
    <Route path="about" component="{About}" />
    <Route path="/"><Home /></Route>
  </main>
</Router>
</div>