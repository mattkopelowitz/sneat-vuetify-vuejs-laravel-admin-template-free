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
      <div class="header">
        <h1>Actual Revenue</h1>
      </div>

      <div class="period-search">
          <label for="period">Period</label>
          <input type="date" id="period">
          <button @click="searchRevenue">
            <box-icon name="search"></box-icon>
          </button>
        </div>

      <table class="revenue-table">
        <thead>
          <tr>
            <th>ID</th>
            <th>Period</th>
            <th>Client</th>
            <th>Deployment Area</th>
            <th>Product</th>
            <th>Amount</th>
            <th>Status</th>
            <th>Notes</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td colspan="8">
              <button @click="togglePopup" class="add-button">
                <box-icon type="solid" name="plus-square"></box-icon>
              </button>
            </td>
          </tr>
        </tbody>
      </table>

      <AddActualRevenuePopup v-if="popupTrigger" :togglePopup="togglePopup">
        <h1>Add Actual Revenue</h1>
      </AddActualRevenuePopup>
    </VWindow>
  </div>
</template>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.period-search {
  display: flex;
  align-items: center;
  gap: 5px;
}

.period-search label {
  font-weight: bold;
}

.period-search input {
  margin-left: 5px;
  padding: 5px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.period-search button {
  background: none;
  border: none;
  cursor: pointer;
}

.revenue-table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 10px;
}

.revenue-table th,
.revenue-table td {
  border: 1px solid #ccc;
  padding: 10px;
  text-align: left;
}

.revenue-table th {
  background-color: #f9f9f9;
}

.add-button {
  background: none;
  border: none;
  cursor: pointer;
  display: flex;
  width: 100%;
  padding: 10px;
}
</style>
