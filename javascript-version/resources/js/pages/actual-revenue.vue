<script setup>
    import { useRoute } from 'vue-router'
    import 'boxicons'
    import AddActualRevenuePopup from '@layouts/components/AddActualRevenuePopup.vue'
    import { ref } from 'vue'

    const route = useRoute();
    const activeTab = ref(route.params.tab);

    const popupTrigger = ref(false);
    const togglePopup = () => {
      popupTrigger.value = !popupTrigger.value;
    }

  
</script>

<template>
    <div>
      <VTabs
        v-model="activeTab"
        show-arrows
      >
        <VTab
          v-for="item in tabs"
          :key="item.icon"
          :value="item.tab"
        >
          <VIcon
            size="20"
            start
            :icon="item.icon"
          />
          {{ item.title }}
        </VTab>
      </VTabs>
      <VDivider />
  
      <VWindow v-model="activeTab" class="mt-5 disable-tab-transition">
      
        <h1>Actual Revenue</h1>
        <div>
          <label for="Period">Period </label>
          <input type="date" placeholder="June 2024">
          <button type="button" @click="searchRevenue">   
                <box-icon type="" name='search'></box-icon>
          </button>
        </div>
        

        <table>
          <tr>
            <th scope="col">ID</th>
            <th scope="col">Period</th>
            <th scope="col">Client</th>
            <th scope="col">Development Area</th>
            <th scope="col">Product</th>
            <th scope="col">Amount</th>
            <th scope="col">Status</th>
            <th scope="col">Notes</th>
          </tr>

          <button type="button" @click="togglePopup">
                <box-icon type='solid' name='plus-square'></box-icon>
          </button>
          
          <tr>
            <th scope="row">
            
            </th>
          </tr>

        </table>

        <div class="Add-Actual-Revenue-Popup">
           <AddActualRevenuePopup v-if="popupTrigger" :togglePopup="() => togglePopup()">
              <h1>Add Actual Revenue</h1>
           </AddActualRevenuePopup>
        </div>
       


        
      </VWindow>
    </div>
  </template>
  