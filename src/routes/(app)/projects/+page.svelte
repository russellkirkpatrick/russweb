<script>
import { base } from '$app/paths';
</script>

<div id="projects-container">
  <div class="projects">
    <a href="github.com/russellkirkpatrick" target="_blank">
      <img class="icons" src="/images/github.jpg" />
    </a>
  </div>

  <div class="projects">
    <a href="{base}/projects/lisbon">Lison City Metrics</a>
  </div>

  <div class="projects">
    <a href="{base}/projects/gridify">Gridify</a>
  </div>
  
  <div class="projects">
    <a href="{base}/projects/web">music web</a>
    <span class="left-spacing">🚧</span>
  </div>

  <div class="projects">
    <a href="{base}/projects/jeans">jeans</a>
    <span class="left-spacing">🚧</span>
  </div>

  <div class="projects">
    <a href="{base}/projects/winery">winery</a>
    <span class="left-spacing">🚧</span>
  </div>

  <div class="projects">
    <a href="{base}/projects/pinterest">pinterest profile widget</a>
    <span class="left-spacing">🚧</span>
  </div>

  
</div>


<style>
  #projects-container {
    margin: 5%;
    margin-top: 2%;
  }

  .projects {
    display: flex;
    align-items: center;
    margin-bottom: 10px;
  }

  .left-spacing {
    margin-left: 10px;
  }

  .icons {
    height: 30px;
    width: 30px;
  }

  
</style>