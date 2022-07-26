<script>
  import { Router, Link, Route } from "svelte-navigator";
  import Login from './pages/Login.svelte'
  import Private from './pages/Private.svelte'
</script>

<Router>
  <div>
<nav style="display: flex;justify-content: space-around;">
    <Link to="/">Login</Link>
    <Link to="redirect">Private page</Link>
</nav>
<br>
      <Route path="/" component={Login} />
      <Route path="redirect" component={Private} />
</div>
</Router>