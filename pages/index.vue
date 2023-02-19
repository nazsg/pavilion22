<template>
  <div class="home">
    <div class="page_container">
      <main>
        <h1>Authentic Thai Cuisine</h1>
        <p class="intro">
          Thailand, the land of smiles and its unique cuisine is the Buddhist
          land in South East Asia, the country which is formerly known as Siam
          has been renamed Thailand since 1939 in the era of King Rama VIII.
          Thailand means the land of freedom. The Thais are proud of their
          country, which has never been a colony of any country. The capital
          city of Thailand is Bangkok.
        </p>
        <section>
          <h2>DINE-IN OR TAKE AWAY</h2>
          <telIcon />
          <a href="tel:01304367707">01304 367 707</a> (click/tap to phone)
          <address>114 HIGH STREET CT14 6BB, DEAL, KENT, UK</address>
          <div class="discount">20% discount <i>on all take-aways</i></div>
        </section>
      </main>

      <aside class itemscope itemtype="http://schema.org/LocalBusiness">
        <!-- <time itemprop="openingHours" datetime="Tu-Su 17:30-23:00" -->
        <span itemprop="openingHours" content="Tu,We,Th,Fr,Sa,Su 17:30-23:00"
          >17:30-23:00 Tuesdays to Sundays</span
        >
        <div>Closed on Mondays</div>
      </aside>
      <div align="center" class="widgetContainer">
        <iframe
          src="https://svtables.com/widget/?rest_id=403"
          style="width: 100%; height: 700px"
        ></iframe>
      </div>
    </div>
  </div>
</template>

<script>
import telIcon from 'vue-material-design-icons/Phone.vue'
export default {
  components: { telIcon },
  head: {
    title: 'Bangkok Pavilion | Thai Restaurant in Deal, Kent',
    meta: [
      {
        hid: 'description',
        name: 'description',
        content: 'Thai restaurant in the high street of Deal in Kent',
      },
    ],
  },
}
</script>
