<template>
  <Layout>
    
    <!-- Learn how to use images here: https://gridsome.org/docs/images -->
    <section>
    <!-- <g-image alt="Example image" src="~/favicon.png" width="135" /> -->
    
    <h1>Hacker News—Using Gridsome.</h1>
   
    <p>
      Lorem ipsum dolor sit amet, consectetur adipisicing elit. Pariatur excepturi labore tempore expedita, et iste tenetur suscipit explicabo! Dolores, aperiam non officia eos quod asperiores
    </p>

    <p class="home-links">
      <a href="https://gridsome.org/docs" target="_blank" rel="noopener">Gridsome Docs</a>
      <a href="https://github.com/gridsome/gridsome" target="_blank" rel="noopener">GitHub</a>
    </p>
    </section>

    <main class="wrapper-main">
      <article v-for="edge in $page.posts.edges" :key="edge.node.id">
        <h2><a :href="edge.node.url || edge.node.link">{{ edge.node.title }}</a>
        <span style="padding-left: 1em;" v-if="edge.node.url">[external]</span>
        <span style="padding-left: 1em;" v-else>[hackernews]</span>
        <span style="padding-left: 1em;" ><a :href="edge.node.link">[comments]</a></span>
        <span style="padding-left: 1em;" >[{{edge.node.points}} ⭐]</span>
        </h2>
      </article>
    </main>

  </Layout>
</template>

<page-query>
query Posts {
  posts: allPosts {
    edges {
      node {
        title
        id
        points
        time
        url
        link
      }
    }
  }
}
</page-query>

<script>
export default {
  metaInfo: {
    title: 'Hello, world!'
  }
}
</script>

<style>
.home-links a {
  margin-right: 1rem;
}
.wrapper-main {
  font-family: 'SF Pro Text', Arial, sans-serif;
  font-size: 16px;
  margin-top: 5em;
}
</style>
