<script>
  import { page } from '$app/stores';
  import { base } from '$app/paths';
  
  let filepath = [];
  let paths = {};

  $: {
    const pathname = $page.url.pathname;

    // strip base from the front of the path if it's there
    const withoutBase =
      base && pathname.startsWith(base)
        ? pathname.slice(base.length)
        : pathname || '/';

    filepath = withoutBase.split('/').filter(Boolean);
    paths = { '/': 'russell' };

    let current = '';
    for (const part of filepath) {
      current += '/' + part;
      paths[current] = part;
    }
  }

  $: labels = Object.values(paths);
</script>

<header>
  <!-- base IS needed for static assets -->
  <img src={`${base}/images/russimg.jpg`} id="user-pfp" />

  {#each Object.entries(paths) as [key, value], i}
    <a href={key} class="left-nav">{value}</a>
    {#if i < Object.entries(paths).length - 1}
      <p>&nbsp;/</p>
    {/if}
  {/each}
</header>

<style>
  header {
    display: flex;
    align-items: center;
    padding-top: 15px;
    padding-left: 23px;
  }


  p {
    font-size: 15px;
  }

  .left-nav {
    margin-left: 15px;
  }

  #user-pfp {
    height: 35px;
    width: 35px;
    border-radius: 100px;
    object-fit: cover;
  }
</style>