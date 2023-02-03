<template>
  <div class="landing-page">
    
      <section class="landing-hero pt-5">
        <div class="header__bg"></div>
        <div class="container mx-auto relative">
          <Navbar/>
          <Hero/>
        </div>
      </section>

      <Steps/>

      <Projects :campaigns="campaigns"/>
    
      <ClientsReact/>

      <div class="cta-clip -mt-20"></div>

      <CallToAction/>
      <Footer/>
    </div>
</template>

<script>
export default {
  name: 'IndexPage',

  //Async Data Pake {axios} Hanya Jalan Di Page, Di Component Gamao
  async asyncData({ $axios }) {
    const campaigns = await $axios.$get('/api/campaigns')
    return { campaigns }
  }
}
</script>
