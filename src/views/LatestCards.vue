<template>
   <div id="features" class="py-4 px-4 lg:px-8 mt-5 mx-0 lg:mx-8 ">
        <div class="flex flex-column text-center mt-8 mb-6">
          <span class="text-600 text-2xl">Our latest listings at a glance</span>
        </div>
        <div class="flex justify-content-center">
          <div class="grid px-2 md:px-0">
            <div class="col-12 lg:col-6 xl:col-4 flex justify-content-evenly" v-for="property in properties" :key="property">
              <Card class="transition-duration-500 shadow-6 hover:shadow-8" v-motion-slide-visible-top :delay="200" @click="() => $router.push('/buy-properties')"
                :hovered="{ y: -10 }">
                <template #header>
                  <img :src="'http://localhost/RealEstateApi/storage/app/public/' + property.image_path" style="height: 18rem" class="border-round-top-2xl" />
                </template>
                <template #title>
                  <div class="text-center" style="color: #45525b; font-size: 20px; font-weight: 600; letter-spacing: 1px">{{ property.name }}</div>
                </template>
                <template #subtitle>
                  <div class="text-center uppercase" style="font-size: 13px; font-weight: 650; letter-spacing: 2px">{{ property.type }}</div>
                </template>
                <template #content>
                  <div class="flex justify-content-between mx-2">
                    <div class="flex align-items-center"><i class="pi pi-building" style="font-size: 1.2rem"></i><span
                        class="text-600 font-medium ml-1">{{property.size}} m<span class="text-sm vertical-align-top">2</span></span>
                    </div>
                    <div class="flex align-items-center"><i class="pi pi-inbox" style="font-size: 1.2rem"></i><span
                        class="text-600 font-medium ml-2">{{property.bathrooms_number}} Bathrooms</span></div>
                    <div class="flex align-items-center"><i class="pi pi-mobile" style="font-size: 1.2rem"></i><span
                        class="text-600 font-medium ml-1">{{property.bedrooms_number}} Rooms</span></div>
                  </div>
                </template>
              </Card>
            </div>
          </div>
        </div>
      </div>

  <div id="highlights" class="py-5 px-5 lg:px-8 mx-0 my-6 lg:mx-7" style="border-radius: 20px">
    <div class="flex flex-column text-center">
      <span class=" text-600 text-2xl">About Us</span>
    </div>

    <div class="grid mt-6 pb-2 md:pb-8" v-motion-slide-visible-right :delay="400">
      <div class="flex justify-content-center col-12 lg:col-6 p-0 flex-order-1 lg:flex-order-0"
        style="border-radius: 8px">
        <img src="/demo/images/product/about.jpg" class="w-full border-round-xl mt-3" alt="mockup mobile" />
      </div>

      <div class="col-12 lg:col-6 my-auto flex flex-column lg:align-items-end text-center lg:text-right">
        <div class="flex align-items-center justify-content-center bg-purple-200 align-self-center lg:align-self-end"
          style="width: 4.2rem; height: 4.2rem; border-radius: 10px">
          <i class="pi pi-fw pi-question-circle text-5xl text-purple-700"></i>
        </div>
        <h2 class="line-height-1 text-900 text-4xl font-normal">Love Where You Live</h2>
        <span class="text-s00 text-2xl line-height-3 ml-0 md:ml-2" style="max-width: 650px">
          We are real estate company known for its expertise, reliability, and exceptional service. With years of
          experience, our dedicated team offers comprehensive solutions for selling properties.
          We pride ourselves on our vast network, enabling us to present a diverse portfolio of residential and commercial
          spaces.
        </span>
      </div>
    </div>
  </div>
</template>
  
<script >
//import Image from 'primevue/image';
import axios from 'axios';
export default{
  data(){
    return{
      properties: [],
      menu: null,


    }
  },
  methods:{
  getAllProperties() {
      axios
        .get(
          "/properties")
        .then((response) => {
          this.properties = response.data.slice(0, 3);
          console.log(this.properties)
        })
        .catch((error) => {
          console.log(error)
        });

        
    }
  },
  mounted() {
    this.getAllProperties()
  }
}



 


</script>


  
<style scoped>
.container {
  max-width: 1200px;
  /* Ograničava širinu sadržaja */
  margin: 0 auto;
  /* Centrira sadržaj na sredini */
}

/* Dodaje razmak između kartica */
.col-md-4 {
  margin: 1rem;
}</style>