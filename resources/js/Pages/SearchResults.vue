<template>
  <div class="landing-page">
    <!-- Include Header -->
    <Header />

    <!-- Hero Section -->
    <section class="hero">
      <img src="/images/Banner.PNG" alt="Hero Background" class="hero-img" />
    </section>

    <!-- Upcoming Events -->
    <section class="upcoming-events">
      <h2>UPCOMING EVENT</h2>
      <div class="events-grid">
        <div class="event-card" v-for="event in events" :key="event.id" @click="goToEventPage(event.id)">
          <h3>{{ event.judul }}</h3>
          <img :src="'/storage/' + event.image" alt="Event Image" />
          <h4>{{ event.deskripsi }}</h4>
          <p>{{ event.tanggal }}</p>
        </div>
      </div>
    </section>

    <div v-if="artworks.length === 0 && events.length === 0" class="no-results">
      No results found for "{{ query }}"
    </div>

    <!-- Footer -->
     <div class="footer-contact">
      <h3>Contact us to show our event folks...</h3>
      <p>terseearoriginal@gmail.com</p>
    </div>
    <Footer />
  </div>
</template>

<script>
import Header from "./Header.vue";
import Footer from "./Footer.vue";
export default {
  name: 'SearchResultsPage',
  components: {
    Header,
    Footer,
  },
  props: {
    query: String,
    artworks: {
      type: Array,
      default: () => []
    },
    events: {
      type: Array,
      default: () => []
    }
  }
}
</script>

<style scoped>
.landing-page {
  background-color: #001B2A;
  background-image: url('/images/background.PNG');
  background-size: cover;
  background-position: center;
  color: #fff;
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  position: relative;
}

.landing-page::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: #000;
  opacity: 0.7;
  mix-blend-mode: darken;
  z-index: 1;
}

.landing-page * {
  position: relative;
  z-index: 2;
}

.hero {
  position: relative;
  text-align: center;
  color: #fff;
}

.hero-img {
  width: 100%;
  height: 400px;
  object-fit: cover;
}

.upcoming-events, .find-community {
  padding: 50px 20px;
  text-align: left;
}

.upcoming-events h2, .find-community h2 {
  color: #FF6B4A;
  font-size: 32px;
  margin-bottom: 20px;
}

.no-results {
  color: #FF6B4A;
  font-size: 32px;
  margin-bottom: 20px;
  margin-left:20px
}


.upcoming-events h3 {
  color: #FF6B4A;
  font-size: 15px;
  font-weight : 400;
}

.find-community h3{
 color: #fff;
  font-size: 25px;
  font-weight : 400;
}

.find-community h4{
 color: #FF6B4A;
  font-size: 15px;
  font-weight : 400;
}
.upcoming-events p {
  color: #FF6B4A;
  font-size: 10px;
  font-weight : 400;
}
.find-community p {
color: #fff;
  font-size: 10px;
  font-weight : 400;
}

.events-grid, .community-grid {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 20px;
}

.event-card, .community-card {
  background: #2B3134;
  padding: 20px;
  border-radius: 10px;
  width: 300px;
  cursor: pointer;
}

.event-card img, .community-card img {
  width: 100%;
  height: 150px;
  object-fit: cover;
  border-radius: 8px;
  margin-bottom: 10px;
}
.footer-contact {
  background: #ff6b4a;
  padding: 20px 10px;
  text-align: center;
  color: #000;
  font-weight: bold;
}
</style>

