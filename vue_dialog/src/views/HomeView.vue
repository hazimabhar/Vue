<template>
  <div class="flex justify-center items-center min-h-screen">
    <div>
      <table class="table-auto mx-auto">
        <thead>
          <tr>
            <th class="px-4 py-2">#</th>
            <th class="px-4 py-2">Brand</th>
            <th class="px-4 py-2">Name</th>
            <th class="px-4 py-2">Year of Manufacture</th>
            <th class="px-4 py-2">Action</th>
          </tr>
        </thead>
        <tbody class="text-center">
          <tr v-for="(car, index) in carList" :key="car.id">
            <td class="border px-4 py-2">{{ index + 1 }}</td>
            <td class="border px-4 py-2">{{ car.make }}</td>
            <td class="border px-4 py-2">{{ car.model }}</td>
            <td class="border px-4 py-2">{{ car.year }}</td>
            <td class="border px-4 py-2">
              <i
                role="button"
                @click="openDetails(car)"
                class="fa-solid fa-eye hover:text-slate-400"
              >
              </i>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
  <DetailsPage :open-dialog="openDialog" :car-details="carDetails" @close-dialog="closeDialog" />
</template>

<script>
import mockData from '../mockData.json'
import DetailsPage from './DetailsPage.vue'

export default {
  components: {
    DetailsPage
  },
  data() {
    return {
      carList: [],
      carDetails: {},
      openDialog: false
    }
  },
  methods: {
    openDetails(car) {
      this.openDialog = true
      this.carDetails = car
    },
    closeDialog() {
      this.openDialog = false
      this.carDetails = {}
    }
  },
  mounted() {
    this.carList = mockData.cars
  }
}
</script>
