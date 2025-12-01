<!-- Home Page -->

<script>
import { base } from '$app/paths';
</script>

<div id="container">
  <div id="user-container">
    <img src="./images/russimg.jpg" id="user-pfp" />
    <p>Russell Kirkpatrick</p>
    <p>Software engineer & designer</p> 
    <p>Nyc</p>
  </div>

  <div id="sections-container">
    <a href="{base}/projects">projects</a>
    <a href="{base}/work">work</a>
    <a href="{base}/life">life</a>
    <a href="{base}/blog">blog</a>
  </div>
</div>

<style>
  #container {
  }

  #user-container {
    display: flex-column;
    align-items: center;
    margin-top: 5%;
    margin-left: 5%;
  }

  #user-pfp {
    height: 200px;
    width: 200px;
    border-radius: 100px;
    object-fit: cover;
  }

  #sections-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    gap: 20px;
  }
</style>