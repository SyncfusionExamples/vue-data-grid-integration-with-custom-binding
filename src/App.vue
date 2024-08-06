<script setup>
import { ref, onMounted, provide } from "vue";
import { GridComponent as EjsGrid, ColumnsDirective as EColumns, ColumnDirective as EColumn, Page, Sort, Filter, Group, LazyLoadGroup, Toolbar, Edit, Search, } from '@syncfusion/ej2-vue-grids';
import { getOrders, addRecord, updateRecord, deleteRecord } from './orderService';

const data = ref([]);
const grid = ref([]);
const groupSettings = { enableLazyLoading: true, columns: ['ProductName'], showGroupedColumn: true, };
const filterSettings = { columns: [{ field: 'CustomerName', matchCase: false, operator: 'startswith', predicate: 'and', value: 'Maria' }] };
const sortSettings = { columns: [{ field: 'ProductID', direction: 'Descending' }] }
const state = { skip: 0, take: 12, group: groupSettings, sort: sortSettings, filter: filterSettings };
const editSettings = { allowEditing: true, allowAdding: true, allowDeleting: true, newRowPosition: 'Top', };
const toolbar = ['Add', 'Edit', 'Delete', 'Update', 'Cancel', 'Search'];
const OrderIDRules = { required: true };

const dataStateChange = function (state) {
    const query = grid.value.getDataModule().generateQuery();
    getOrders(state, query).then(gridData => {
      data.value = gridData.result; // Assign the result to the data property
    });
  }

const dataSourceChanged = function (state) {
  if (state.action === 'add') {
    addRecord(state.data, state); state.endEdit();
  } else if (state.action === 'edit') {
    updateRecord(state.data, state); state.endEdit();
  } else if (state.requestType === 'delete') {
    deleteRecord(state.data[0].OrderID, state); state.endEdit();
  }
}

onMounted(() => {
  dataStateChange(state);
});

provide('grid', [Page, Filter, Sort, Group, LazyLoadGroup, Toolbar, Edit, Search]);
</script>

<template>
  <ejs-grid ref="grid" :dataSource='data' :allowPaging='true' :allowFiltering='true' :filterSettings='filterSettings'
    :allowSorting='true' :sortSettings='sortSettings' :allowGrouping='true' :groupSettings='groupSettings'
    :toolbar='toolbar' :editSettings='editSettings' :dataStateChange="dataStateChange"
    :dataSourceChanged="dataSourceChanged">
    <e-columns>
      <e-column field='OrderID' headerText='Order ID' width='90' textAlign='Right' isPrimaryKey='true'
        :validationRules="OrderIDRules"></e-column>
      <e-column field="CustomerName" headerText="Customer Name" width="100"></e-column>
      <e-column field='ProductID' headerText='Product ID' width=100></e-column>
      <e-column field='ProductName' headerText='Product Name' format='C2' width=100></e-column>
    </e-columns>
  </ejs-grid>
</template>

<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/tailwind.css";
  @import "../node_modules/@syncfusion/ej2-buttons/styles/tailwind.css";
  @import "../node_modules/@syncfusion/ej2-calendars/styles/tailwind.css";
  @import "../node_modules/@syncfusion/ej2-dropdowns/styles/tailwind.css";
  @import "../node_modules/@syncfusion/ej2-inputs/styles/tailwind.css";
  @import "../node_modules/@syncfusion/ej2-navigations/styles/tailwind.css";
  @import "../node_modules/@syncfusion/ej2-popups/styles/tailwind.css";
  @import "../node_modules/@syncfusion/ej2-splitbuttons/styles/tailwind.css";
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/tailwind.css";
</style>