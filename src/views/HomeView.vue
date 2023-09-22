<template>
    <!--Za Pocetni izgled-->
    <div class="home">

        <div class="grid grid-nogutter surface-section text-800">
            <div class="col-12 md:col-6 p-6 text-center md:text-left flex align-items-center">
                <section>
                    <span class="block text-6xl font-bold mb-1">Create the screens your</span>
                    <div class="text-6xl text-indigo-600 font-bold mb-3"> visitors deserve to see!</div>
                    <p class="mt-0 mb-4 text-700 line-height-3">Lorem ipsum dolor sit amet, consectetur adipiscing elit,
                        sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>

                        <a href="/buy-properties"><Button label="All Properties" raised class="button  " id="button1"  /></a>
                        <!--<a href="/all-properties"><Button label="List your property" class="button " id="button2" raised /></a>-->
                </section>
            </div>
            <div class="col-12 md:col-6 overflow-hidden">
                <Image src="https://primefaces.org/cdn/primevue/images/galleria/galleria7.jpg" alt="Image"
                    class="md:ml-auto block md:h-full" style="clip-path: polygon(8% 0, 100% 0%, 100% 100%, 0 100%)" />
            </div>
        </div>


    </div>
    <!--Kartice-->
    <div>
        <LatestCards/>
    </div>

    <!--Footer-->
    <div class="py-4 px-4 mx-0 mt-8 lg:mx-8 ">
                <div class="grid justify-content-between">
                    <div class="col-12 md:col-2" style="margin-top: -1.5rem">
                        <a @click="smoothScroll('#home')" class="flex flex-wrap align-items-center justify-content-center md:justify-content-start md:mb-0 mb-3 cursor-pointer">
                            <img src="demo/images/product/8207.jpg" alt="footer sections" width="350" height="350" class="mr-2" />
                            
                        </a>
                    </div>

                    <div class="col-12 md:col-10 lg:col-7">
                        <div class="grid text-center md:text-left">
                            <div class="col-12 md:col-3">
                                <h4 class="font-medium text-2xl line-height-3 mb-3 text-900">Company</h4>
                                <a class="line-height-3 text-xl block cursor-pointer mb-2 text-700">About Us</a>
                                <a class="line-height-3 text-xl block cursor-pointer mb-2 text-700">News</a>
                                <a class="line-height-3 text-xl block cursor-pointer mb-2 text-700">Investor Relations</a>
                                <a class="line-height-3 text-xl block cursor-pointer mb-2 text-700">Careers</a>
                                <a class="line-height-3 text-xl block cursor-pointer text-700">Media Kit</a>
                            </div>

                            <div class="col-12 md:col-3 mt-4 md:mt-0">
                                <h4 class="font-medium text-2xl line-height-3 mb-3 text-900">Resources</h4>
                                <a class="line-height-3 text-xl block cursor-pointer mb-2 text-700">Get Started</a>
                                <a class="line-height-3 text-xl block cursor-pointer mb-2 text-700">Learn</a>
                                <a class="line-height-3 text-xl block cursor-pointer text-700">Case Studies</a>
                            </div>

                            <div class="col-12 md:col-3 mt-4 md:mt-0">
                                <h4 class="font-medium text-2xl line-height-3 mb-3 text-900">Community</h4>
                                <a class="line-height-3 text-xl block cursor-pointer mb-2 text-700">Discord</a>
                                <a class="line-height-3 text-xl block cursor-pointer mb-2 text-700">Events<img src="/demo/images/landing/new-badge.svg" class="ml-2" /></a>
                                <a class="line-height-3 text-xl block cursor-pointer mb-2 text-700">FAQ</a>
                                <a class="line-height-3 text-xl block cursor-pointer text-700">Blog</a>
                            </div>

                            <div class="col-12 md:col-3 mt-4 md:mt-0">
                                <h4 class="font-medium text-2xl line-height-3 mb-3 text-900">Legal</h4>
                                <a class="line-height-3 text-xl block cursor-pointer mb-2 text-700">Brand Policy</a>
                                <a class="line-height-3 text-xl block cursor-pointer mb-2 text-700">Privacy Policy</a>
                                <a class="line-height-3 text-xl block cursor-pointer text-700">Terms of Service</a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        

    
</template>

<script setup>
import Button from 'primevue/button';
import Image from 'primevue/image';

import LatestCards from './LatestCards.vue';


</script>

<style scoped>
.home {
    margin-top: 50px;


}

#button1 {
    margin-right: 10px;
    color: #ffffff;
    background-color: #4E5FBB;
    padding: 0.5rem 1rem;
    border-radius: 0.5rem;
    font-weight: bold;
    font-size: 1rem;
    text-align: center;
    cursor: pointer;
}

#button1:hover {
    background-color: rgb(75, 66, 196);
    /* Dodajte stil za hover prema vašim preferencijama */
}

#button1:focus {
    outline: none;
    box-shadow: 0 0 0 4px rgba(0, 0, 255, 0.3);
    /* Dodajte stil za fokus prema vašim preferencijama */
}

#button2 {
    color: #3f51b5;
    background-color: #fff;
    padding: 0.5rem 1rem;
    border: 2px solid #3F51B5;
    border-radius: 0.5rem;
    font-weight: bold;
    font-size: 1rem;
    text-align: center;
    cursor: pointer;
}

#button2:hover {
    background-color: rgb(174, 153, 187);
    /* Dodajte stil za hover prema vašim preferencijama */
}

#button2:focus {
    outline: none;
    box-shadow: 0 0 0 4px rgba(0, 0, 255, 0.3);
    /* Dodajte stil za fokus prema vašim preferencijama */
}
</style>