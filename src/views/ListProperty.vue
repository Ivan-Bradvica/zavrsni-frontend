<template>
    <div class="form-demo">
        <Toast position="top-right" />
        <div class="
          surface-ground
          flex
          align-items-center
          justify-content-center
          min-h-screen min-w-screen
          overflow-hidden
        ">
            <div class="
            flex flex-column
            align-items-center
            justify-content-center
            px-2
            md:px-0
          ">
                 <div>
                    <div class="w-full surface-card py-8 px-8" style="border-radius: 53px">
                        <div class="text-center mb-5">
                            <div class="text-900 text-3xl font-medium mb-3">Welcome!</div>
                         </div>

                         <form class="p-fluid ">
                            <div class="field">
                                <div class="p-float-label mt-5 p-input-icon-right">
                                    <i class="pi pi-user" />
                                    <InputText id="name" />
                                    <label for="name">Name*</label>
                                </div>
                                <small class="p-error"></small>
                            </div>

                            <div class="field">
                                <div class="p-float-label mt-5">
                                    <InputText id="surname" />
                                    <label for="surname">Owner info*</label>
                                </div>
                                <small class="p-error"></small>
                            </div>

                            <div class="field">
                                <div class="p-float-label mt-4 p-input-icon-right">
                                     <Textarea id="username" />
                                    <label>Details*</label>
                                </div>
                                <small class="p-error"></small>
                            </div>

                            <div class="field">
                                <div class="p-float-label p-input-icon-right mt-4">
                                    <i class="pi pi-envelope" />
                                    <InputText id="email" aria-describedby="email-error" />
                                    <label for="email">Owner Email*</label>
                                </div>
                                <span>
                                    <span>
                                        <small class="p-error"></small>
                                    </span>
                                </span>
                                <small class="p-error"></small>
                            </div>
                            
                             
                            <div class="field-checkbox">
                                <Checkbox id="accept" name="accept" value="Accept" />
                                <label for="accept">I agree to the terms and conditions*</label>
                            </div>
                            <Button label="Submit" class="p-button-rounded p-button-info mr-2 mb-2" />
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
  
<script setup>
import InputText from 'primevue/inputtext';
import Button from 'primevue/button';
 import Checkbox from 'primevue/checkbox';
 import Toast from 'primevue/toast';
 import Textarea from 'primevue/textarea';
</script>
  
<style  scoped>
 

 
</style>