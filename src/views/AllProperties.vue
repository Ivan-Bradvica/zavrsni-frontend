<template>
    <div>
      <InputText v-model="searchText" placeholder="Search" />
      <Dropdown v-model="selectedCategory" :options="categories" optionLabel="name" placeholder="Select a category" />
      <!-- Ostali filteri -->
      <DataTable :value="filteredProducts">
        <Column field="name" header="Name" />
        <Column field="price" header="Price" />
        <Column header="Image">
          <template #body="slotProps">
            <img :src="slotProps.data[slotProps.index].imageUrl" alt="Product Image" />
          </template>
        </Column>
        <!-- Ostali stupci -->
      </DataTable>
    </div>
  </template>
  
  <script setup>
  import InputText from 'primevue/inputtext';
  import DataTable from 'primevue/datatable';
   import Dropdown from 'primevue/dropdown';
   import Column from 'primevue/column';
 
  </script>
  