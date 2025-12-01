<script>
  import { page } from '$app/stores';
  import { base } from '$app/paths';
  
  let paths = {}

  $: {
    // 1. Remove the "base" (e.g. /russweb) from the path so we can split it cleanly
    const cleanPath = $page.url.pathname.replace(base, '');
    
    // 2. Split the remaining path into segments
    const segments = cleanPath.split("/").filter(Boolean);

    // 3. Start the object with the Home link
    // If base exists, home is '/russweb', otherwise it's '/'
    paths = { [base || '/']: "russell" }

    let current = base;

    for (const part of segments) {
      current += "/" + part
      paths[current] = part
    }
  }
</script>

<header>
  <img src="{base}/images/russimg.jpg" id="user-pfp"/>
  
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