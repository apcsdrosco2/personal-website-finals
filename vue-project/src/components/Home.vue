<template>
  <div class="container">
    <div class="sidebar">
      <div v-for="section in sections" :key="section.id" @click="activeSection = section.id">
        <img :src="section.img" :alt="section.name" />
        <span>{{ section.name }}</span>
      </div>
    </div>

    <div class="content">
      <section v-for="section in sections" :key="section.id" v-show="activeSection === section.id">
        <h2>{{ section.name }}</h2>
        <div v-html="section.content"></div>
      </section>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      activeSection: 'about-me',
      sections: [
        { id: 'about-me', name: 'About Me', img: 'buttons/about-me.png', content: `<p>I've never really liked my name... <br> MBTI TYPE: INTP-T...</p>` },
        { id: 'education', name: 'Education', img: 'buttons/education.png', content: `<p>ELEMENTARY: Silangan Elementary School...</p>` },
        { id: 'it-experience', name: 'IT Experience', img: 'buttons/it-experience.png', content: `<p>PROJECTS: HTML Website Building...</p>` },
        { id: 'hobbies', name: 'Hobbies', img: 'buttons/hobbies.png', content: `<p>I enjoy learning guitar...</p>` },
        { id: 'goals', name: 'Goals', img: 'buttons/goals.png', content: `<p>I want to graduate on time...</p>` },
        { id: 'favorites', name: 'Favorites', img: 'buttons/favorites.png', content: `<h3>PLAYLIST</h3> <iframe src='https://open.spotify.com/embed/playlist/6bV6j6crruknzq3H7DNTMs'></iframe>` },
        { id: 'gallery', name: 'Gallery', img: 'buttons/gallery.png', content: `<p>Access this link to see my gallery: <a href='https://apcsdrosco2.github.io/WEBPROGSS231-personal-website/home/gallery.html'>Gallery</a></p>` },
        { id: 'comments', name: 'Comments', img: 'buttons/comments.png', content: `<p></p>` }
      ]
    };
  }
};
</script>

<style scoped>
.container {
  display: flex;
}
.sidebar {
    position: fixed; 
    top: 0;
    left: 0;
    width: 250px; 
    height: 100vh; 
    background-color: #FFFFF; 
    color: black;
    display: flex;
    flex-direction: column;
    padding-top: 20px; 
    box-shadow: 2px 0 5px rgba(0, 0, 0, 0.2);
    overflow-y: auto;
}
.sidebar div {
  cursor: pointer;
  display: flex;
  align-items: center;
  padding: 10px;
}
.sidebar img {
  width: 30px;
  margin-right: 10px;
}
.content {
  flex: 1;
  margin-left: 250px;
  padding: 20px;
}
.hidden-section {
  display: none;
}
</style>
