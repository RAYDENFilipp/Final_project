<script>
  import { deleteCookie, sendData } from "../../utilities/helperFunctions";
  import { submitType, userLoggedIn, pagePicked } from "../../utilities/stores";
  export let collapsed = true;

  let links = [
    { active: true, href: "#home", text: "Home" },
    { active: false, href: "#about", text: "About" },
    { active: false, href: "#contacts", text: "Contacts" }
  ];
  // links get highlighted on select
  function handleClick(active, href, e) {
    if (!active) {
      links = links.map(link => {
        link.active =
          link.href === href || link.active ? !link.active : link.active;
        return link;
      });
    }
    // used for selective rendering on the App component
    pagePicked.set(href);
  }
</script>

<style>
  @media (min-width: 768px) {
    li {
      border-right: 0.2rem solid;
      min-width: 5rem;
    }

    li:first-child {
      border-left: 0.2rem solid;
    }
  }
</style>

<div class:collapse={collapsed} class="navbar-collapse">
  <ul class="navbar-nav mr-auto">
    {#each links as { active, href, text }}
      <li class:active class="nav-item border-light text-md-center">
        <a class="nav-link" {href} on:click={e => handleClick(active, href, e)}>
          {text}
          {#if active}
            <span class="sr-only">(current)</span>
          {/if}
        </a>
      </li>
    {/each}
  </ul>
  <div class="form-inline mt-2 mt-md-0 mr-lg-2">
    <!-- selective rendering of login buttons depending on wheter user logged in or not -->
    {#if $submitType === 'Sign Out'}
      <!-- clears the cookie and the stores -->
      <button
        class="btn btn-outline-danger my-2 my-sm-0"
        on:click={() => {
          deleteCookie('user_id', -5);
          submitType.set('');
          sendData(`/users/${$userLoggedIn}`, 'PATCH', { logged_in: false });
          userLoggedIn.set(null);
        }}>
        Sign out
      </button>
    {:else}
      <!-- opens a 'Sign In' modal -->
      <button
        class="btn btn-outline-light mr-sm-2"
        on:click={() => submitType.set('Sign In')}>
        Sign In
      </button>
      <!-- opens a 'Sign Up' modal -->
      <button
        class="btn btn-outline-light my-2 my-sm-0"
        on:click={() => submitType.set('Sign Up')}>
        Sign Up
      </button>
    {/if}
  </div>
</div>
