<template>
    <section class="container mx-auto pt-24">
        <div class="flex justify-between items-center">
          <div class="w-auto">
            <h2 class="text-3xl text-gray-900 mb-8">
              New projects you can <br />
              taken care of
            </h2>
          </div>
          <div class="w-auto mt-5">
            <a class="text-gray-900 hover:underline text-md font-medium" href=""
              >View All</a
            >
          </div>
        </div>

        <div class="grid grid-cols-3 gap-4 mt-3">

          <div class="card-project w-full p-5 border border-gray-500 rounded-20" style="height: 900px" v-for="campaign in campaigns.data" :key="campaign.id">
            <div class="item" >
              <figure class="item-image">
                <img :src="$axios.defaults.baseURL + campaign.image_url" alt="" class="rounded-20 w-full"/>
              </figure>
              <div class="item-meta">
                <h4 class="text-3xl font-medium text-gray-900 mt-5">
                  {{ campaign.name }}
                </h4>
                <p class="text-md font-light text-gray-900 h-12">
                  {{ campaign.short_description }}
                </p>
                <div class="relative pt-4 progress-bar">
                  <div class="overflow-hidden h-2 mb-4 text-xs flex rounded bg-gray-200 h-3 rounded-lg">
                    <div :style="'width:' + ((campaign.current_amount / campaign.goal_amount) * 100)+'%'" class="shadow-none flex flex-col text-center whitespace-nowrap text-white justify-center bg-purple-progress progress-striped"></div>
                  </div>
                </div>
                <div class="flex progress-info">
                  <div>{{ (campaign.current_amount / campaign.goal_amount) * 100 }}%</div>
                  <div class="ml-auto font-semibold">Rp {{ new Intl.NumberFormat().format(campaign.goal_amount) }}</div>
                </div>
              </div>
              <button @click="$router.push({name: 'projects-id', params: {id : campaign.id}})" class="text-center mt-5 button-cta block w-full bg-orange-button hover:bg-green-button text-white font-semibold px-6 py-2 text-lg rounded-full">
                Fund Now
              </button>
            </div>
          </div>

        </div>
      </section>
</template>

<script>
export default {
  name: 'Projects',
  props: {
    campaigns: Object
  }

  // mounted() {
  //   this.getCampaign()
  // },
  // data() {
  //   return {
  //     campaigns: Object
  //   }
  // },
  // methods: {
  //   async getCampaign() {
  //     const campaign = await this.$axios.$get('/api/campaigns')
  //     this.campaigns = campaign
  //     console.log(campaign)
  //   }
  // },

}
</script>