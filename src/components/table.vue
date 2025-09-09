<template>
  <div class="flex flex-col gap-4">

    <div class="w-full">
    <!-- Tabelle -->
      <DataTable :value="emissions" sortMode="multiple" v-model:filters="filters" filterDisplay="row" :globalFilterFields="['company','country']" paginator :rows="5" :rowsPerPageOptions="[5, 10, 15, 20]" showGridlines >
        
        <Column field="place" header="Platz" sortable style="width: 25%">
          <template #filter="{ filterModel, filterCallback }">
            <InputText v-model="filterModel.value" type="text" @input="filterCallback()" placeholder="Search by place" />
          </template>
        </Column>

        <Column field="company" header="Firma" sortable style="width: 25%">
          <template #filter="{ filterModel, filterCallback }">
            <InputText v-model="filterModel.value" type="text" @input="filterCallback()" placeholder="Search by company" />
          </template>
        </Column>

        <Column field="country" header="Land" sortable style="width: 25%">
          <template #filter="{ filterModel, filterCallback }">
            <InputText v-model="filterModel.value" type="text" @input="filterCallback()" placeholder="Search by country" />
          </template>
        </Column>

        <Column field="emissions" header="Emissionen (kt)" sortable style="width: 25%"></Column>
      </DataTable>
    </div>

  </div>

</template>

<script>
import DataTable from 'primevue/datatable';
import Column from 'primevue/column';
import { FilterMatchMode } from '@primevue/core/api';
import InputText from 'primevue/inputtext';
import emissions from '../data/emissions.json';


export default {
  components: { 
    DataTable, 
    Column,
    InputText,
  },

  data() {
    return {
      emissions,
      filters: {
        place: { value: null, matchMode: FilterMatchMode.STARTS_WITH},
        company: { value: null, matchMode: FilterMatchMode.STARTS_WITH },
        country: { value: null, matchMode: FilterMatchMode.STARTS_WITH },
      }
    }
  }
}
</script>