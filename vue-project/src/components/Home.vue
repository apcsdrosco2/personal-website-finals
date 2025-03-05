<template>
  <div class="container">
    <!-- Sidebar Navigation -->
    <div class="sidebar">
      <div v-for="section in sections" :key="section.id" @click="activeSection = section.id">
        <img :src="section.img" :alt="section.name" />
        <span>{{ section.name }}</span>
      </div>
    </div>

    <!-- Content Area -->
    <div class="content">
      <section 
        v-for="section in sections" 
        :key="section.id" 
        v-show="activeSection === section.id"
        :class="['section-bg', section.id]"
      >
        <h2>{{ section.name }}</h2>
        <div v-html="section.content"></div>
      </section>

      <!-- Show Comments.vue when 'comments' section is selected -->
      <Comments v-if="activeSection === 'comments'" />
    </div>
  </div>
</template>


<script>
import Comments from "../components/Comments.vue"; // Import the Comments component
# import css here
export default {
  components: { Comments }, // Register Comments component
  data() {
    return {
      activeSection: "about-me",
      sections: [
        { id: "about-me", name: "About Me", img: "buttons/about-me.png", class: "about-bg", content: 
        `<p>Hi! I'm Suzanne Marie, a student from BSCS-SS and you are here to get to know me... or not <br>
                MBTI TYPE: INTP-T
                <br>
                ZODIAC SIGN: VIRGO
                <br>
              
                </p>` },
        { id: "education", name: "Education", img: "buttons/education.png", content: 
        `<p>ELEMENTARY: <br> 
                SILANGAN ELEMENTARY SCHOOL <br>
                <br>
                JHS/SHS: <br>
                UPPER BICUTAN NATIONAL HIGHSCHOOL - WITH HONOR (GRADE 7-11), GRADUATED WITH HIGH HONORS <br>
                <br>
                COLLEGE: <br>
                ASIA PACIFIC COLLEGE - FIRST YEAR HONOR LISTER.
                </p>` },
        { id: "it-experience", name: "IT Experience", img: "buttons/it-experience.png", content: 
        `<p>PROJECTS: <br>
                <br>
                HTML Website Building (Grade 9) <br>
                - I built an webpage entirely out of HTML that gives all information about previous presidents in the Philippines and their greatest contribution to the country.
                <br>
                EarthCare (1st Year) <br>
                - A final requirement for the subject PROGCON where it prompts random tasks involving taking care of the environment, then gives out usable points for the user to use as voucher. <br>
                <br>
                GAMING: <br>
                ML (ign: /su:'zæn/_131) <br>
                - Inactive since 2024 <br>
                Roblox (ign: shotdeadoverthehead) <br>
                - Since 2021 <br>
                Valorant (ign: shotdeadoverhead #MUAH) <br>
                - Since 2024 
                </p>` },
        { id: "hobbies", name: "Hobbies", img: "buttons/hobbies.png", content: 
        `<p>I enjoy learning new guitar pieces (just from watching youtube videos ⚠️not a professional) <br>
                Listening to music <br>
                Writing poems <br>
                Watching/reading <br>
                Playing video games <br>
                Baking <br>
                <br>
                Things I want to be able to do are : <br>
                Riding a bike <br>
                Draw
                </p>` },
        { id: "goals", name: "Goals", img: "buttons/goals.png", content: `<p>I want to be able to graduate on time, get a decent paying job, and then get a vacation to somewhere where there are four seasons in a year.</p>` },
        { id: "favorites", name: "Favorites", img: "buttons/favorites.png", content: 
        `<h3>PLAYLIST</h3>
            <p>I have this thing that when I really like a movie or series, I make a playlist for me to remember them by.</p>
            <div id="anne">
            <iframe 
                style="border-radius:12px" 
                src="https://open.spotify.com/embed/playlist/6bV6j6crruknzq3H7DNTMs?utm_source=generator" 
                width="500" height="300" frameBorder="0" allowfullscreen="" 
                allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy">
            </iframe>
            </div>
            <div id="hilda">
            <iframe 
                style="border-radius:12px" 
                src="https://open.spotify.com/embed/playlist/0iXro53fNRXLACxLrYgXvK?utm_source=generator" 
                width="500" height="300" frameBorder="0" allowfullscreen="" 
                allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy">
            </iframe>
            </div>
            <div id="timebomb">
            <iframe 
                style="border-radius:12px" 
                src="https://open.spotify.com/embed/playlist/61m22Pnc53j7ygP3YYIf9x?utm_source=generator" 
                width="500" height="300" frameBorder="0" allowfullscreen="" 
                allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy">
            </iframe>
            </div>
            <h3>TRACKS OF 2024</h3>
                <p>(based on my spotify wrapped)<br>
                    Feel free to play them! 
                </p>
                <div id="unknown">
                    <h1> 1. Unknown/nth - Hozier</h1>
                        <iframe 
                            style="border-radius:12px" 
                            src="https://open.spotify.com/embed/track/05QGaQnoBuda27vXxpuiRU?utm_source=generator" 
                            width="300" height="300" frameBorder="0" allowfullscreen="" 
                            allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy">
                        </iframe>
                </div>
                <div id="cherrywine">
                    <h1> 2. Cherry Wine - Hozier</h1>
                        <iframe 
                            style="border-radius:12px" 
                            src="https://open.spotify.com/embed/track/4Q66chx9WzqWcLItXoZ5r4?utm_source=generator" 
                            width="300" height="300" frameBorder="0" allowfullscreen="" 
                            allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy">
                        </iframe>
                </div>
                <div id="psa">
                    <h1> 3. Para sa Akin - Sitti</h1>
                        <iframe 
                            style="border-radius:12px" 
                            src="https://open.spotify.com/embed/track/0MqkYdGBzHx7lnaFvo7doR?utm_source=generator" 
                            width="300" height="300" frameBorder="0" allowfullscreen="" 
                            allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy">
                        </iframe>
                </div>
                <div id="silversprings">
                    <h1> 4. Silver Springs - Fleetwood Mac</h1>

                        <iframe 
                            style="border-radius:12px" 
                            src="https://open.spotify.com/embed/track/1QEzs30PUAJJPbHL1e4NYH?utm_source=generator" 
                            width="300" height="300" frameBorder="0" allowfullscreen="" 
                            allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy">
                        </iframe>
                </div>
                <div id="diwn">
                    <h1> 5. Do I Wanna Know? (cover) - Hozier</h1>

                        <iframe 
                            style="border-radius:12px" 
                            src="https://open.spotify.com/embed/track/3Tgv4rvWBVwnbmUTlJwzk0?utm_source=generator" 
                            width="300" height="300" frameBorder="0" allowfullscreen="" 
                            allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy">
                        </iframe>
                </div>` },
        { id: "gallery", name: "Gallery", img: "buttons/gallery.png", content: `<p>Access this link to see my gallery: <a href='https://apcsdrosco2.github.io/WEBPROGSS231-personal-website/home/gallery.html'>Gallery</a></p>` },
        { id: "comments", name: "Comments", img: "buttons/comments.png", content: "" } 
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
    background-color: #FFFFFF; 
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
  margin-left: 225px;
  padding: 0px;
}
  
</style>
