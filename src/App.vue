<script setup>
import Button from "primevue/button";

import DataTable from "primevue/datatable";
import Column from "primevue/column";
import ColumnGroup from "primevue/columngroup"; // optional
import Row from "primevue/row"; // optional

import { faker } from "@faker-js/faker";

import "primeicons/primeicons.css";

const employeeLists = Array.from({ length: 150 }, () => ({
  image: faker.image.avatar(),
  name: faker.person.fullName(),
  location: faker.location.city(),
  email: faker.internet.email(),
  phone: faker.phone.number("+959#########"),
  department: faker.commerce.department(),
  employeeCode: faker.number.int({ min: 100, max: 999 }),
  // customTags: faker.person.jobTitle(),
  customTags: "Intern",
  positions: "UX Designer",
  nrc: "12/PABATA(N)44444",
  manager: "Zayer Zay",
  managerPosition: "CEO",
  joinnedDate: "12.2.2021",
  terminateDate: "-",
}));
</script>

<template>
  <div class="flex">
    <div class="min-w-[64px] bg-gray-200 flex flex-col justify-between">
      <div class="sticky top-0">
        <img src="../public/image/logo.png" width="64px" height="64px" />
        <div class="flex flex-col gap-5 items-center mt-2">
          <i class="pi pi-desktop"></i>
          <i class="pi pi-clock"></i>
          <i class="pi pi-briefcase"></i>
          <i class="pi pi-stopwatch"></i>
          <i class="pi pi-user"></i>
          <i class="pi pi-sync"></i>
          <i class="pi pi-bell"></i>
          <i class="pi pi-calendar"></i>
          <i class="pi pi-whatsapp"></i>
          <i class="pi pi-ellipsis-h"></i>
          <p class="text-sm -mt-6">more</p>
        </div>
      </div>
      <div class="sticky bottom-0 flex flex-col items-center gap-3">
        <i class="pi pi-file-arrow-up"></i>
        <i class="pi pi-address-book"></i>
        <img
          :src="`https://primefaces.org/cdn/primevue/images/avatar/ionibowcher.png`"
          style="width: 24px"
        />
      </div>
    </div>
    <div class="min-w-[200px] bg-gray-100 px-5 ">
      <div class="flex flex-col gap-6 sticky top-0">
      <h1 class="font-bold text-lg mt-7">Employees</h1>
      <p class="text-green-500">Directory</p>
      <p>Update Request</p>
      <p>Reporting Lines</p>
      <p>Department structures</p>
    </div>
    </div>
    
    <div class="grow px-6 overflow-x-hidden">
      <div class="flex justify-between p-5">
        <div>
          <i class="pi pi-arrow-left"></i>
          <span class="mx-5 text-xl">ceo</span>
          <i class="pi pi-filter-fill mr-5"></i>
          <i class="pi pi-search"></i>
        </div>
        <div>
          <Button label="Create Employee" />
          <i class="pi pi-ellipsis-v ml-3"></i>
        </div>
      </div>
      <DataTable
        :value="employeeLists"
        stripedRows
        scrollable
        scrollWidth="60rem"
        paginator
        :rows="50"
        :rowsPerPageOptions="[50, 75, 100]"
      >
        <Column
          selectionMode="multiple"
          frozen
          alignFrozen="left"
        ></Column>
        <Column field="name" header="Employees" frozen alignFrozen="left" style="min-width: 200px;">
          <template #body="slotProps">
            <div class="flex items-center gap-2">
              <img
                alt="flag"
                :src="`https://primefaces.org/cdn/primevue/images/avatar/ionibowcher.png`"
                style="width: 24px"
              />
              <span>{{ slotProps.data.name }}</span>
            </div>
          </template>
        </Column>
        <Column field="location" header="Location"></Column>
        <Column field="phone" header="Phone"></Column>
        <Column field="email" header="Email"></Column>
        <Column field="department" header="Department"></Column>
        <Column field="employeeCode" header="EmployeeCode"></Column>
        <Column field="customTags" header="CustomTags"></Column>
        <Column field="positions" header="Positions"></Column>
        <Column field="nrc" header="Nrc"></Column>
        <Column field="manager" header="Manager"></Column>
        <Column field="managerPosition" header="ManagerPosition"></Column>
        <Column field="joinnedDate" header="JoinnedDate"></Column>
        <Column field="terminateDate" header="TerminateDate"></Column>
      </DataTable>
    </div>
  </div>
</template>

<style scoped>
/* import 'datatables.net-dt/css/jquery.dataTables.css'; */
th,
td {
  min-width: 140px;
}
td:first-child {
  background-color: brown;
}
</style>
