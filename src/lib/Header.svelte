<script>
  import { page } from '$app/stores';
  import { base } from '$app/paths';

  let paths = {};

  $: {
    const pathname = $page.url.pathname;

    // STEP 1 — remove the base from pathname for breadcrumb logic
    const relative =
      base && pathname.startsWith(base)
        ? pathname.slice(base.length)
        : pathname;

    // STEP 2 — break the remaining path into segments
    const segments = relative.split('/').filter(Boolean);

    // STEP 3 — build final absolute hrefs INCLUDING the base
    paths = {};

    // home breadcrumb (must always start with base in prod)
    const homeHref = base || '/';
    paths[homeHref] = 'russell';

    let current = '';
    for (const part of segments) {
      current += '/' + part;
      const fullHref = `${base}${current}`;
      paths[fullHref] = part;
    }
  }
</script>

<header>
  <img src={`${base}/images/russimg.jpg`} id="user-pfp" />

  {#each Object.entries(paths) as [href, label], i}
    <a href={href} class="left-nav">{label}</a>
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