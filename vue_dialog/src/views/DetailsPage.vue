<template>
  <div v-if="openDialog">
    <div class="relative z-10" aria-labelledby="modal-title" role="dialog" aria-modal="true">
      <div class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity"></div>
      <div class="fixed inset-0 z-10 w-screen overflow-y-auto">
        <div
          class="flex min-h-full items-end justify-center p-4 text-center sm:items-center sm:p-0"
        >
          <div
            class="relative transform overflow-hidden rounded-lg bg-white text-left shadow-xl transition-all sm:my-8 sm:w-full sm:max-w-lg"
          >
            <div class="bg-white px-4 pb-4 pt-5 sm:p-6 sm:pb-4">
              <div class="sm:flex sm:items-start">
                <div
                  class="mx-auto flex h-12 w-12 flex-shrink-0 items-center justify-center rounded-full bg-slate-300 sm:mx-0 sm:h-10 sm:w-10"
                >
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    fill="none"
                    viewBox="0 0 24 24"
                    stroke-width="1.5"
                    stroke="#6e6e6e"
                    class="size-6"
                  >
                    <path
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      d="m11.25 11.25.041-.02a.75.75 0 0 1 1.063.852l-.708 2.836a.75.75 0 0 0 1.063.853l.041-.021M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Zm-9-3.75h.008v.008H12V8.25Z"
                    />
                  </svg>
                </div>
                <div class="mt-3 text-center sm:ml-4 sm:mt-0 sm:text-left">
                  <div class="flex justify-between pb-2">
                    <h3 class="text-base font-semibold leading-6 text-gray-900" id="modal-title">
                      Car Details
                    </h3>
                    <div>
                      <span @click="closeDialog" role="button" class="hover:text-slate-400">
                        <svg
                          xmlns="http://www.w3.org/2000/svg"
                          fill="none"
                          viewBox="0 0 24 24"
                          stroke-width="1.5"
                          stroke="currentColor"
                          class="size-6"
                        >
                          <path
                            stroke-linecap="round"
                            stroke-linejoin="round"
                            d="M6 18 18 6M6 6l12 12"
                          />
                        </svg>
                      </span>
                    </div>
                  </div>
                  <hr class="border-gray-500" />
                  <div class="py-3">
                    <div class="grid grid-cols-4 gap-4">
                      <div class="mt-2">
                        <p class="text-sm text-gray-500">Manufacture:</p>
                      </div>
                      <div class="mt-2">
                        <p class="text-sm text-black">{{ carDetails.make }}</p>
                      </div>
                      <div class="mt-2">
                        <p class="text-sm text-gray-500">Model:</p>
                      </div>
                      <div class="mt-2">
                        <p class="text-sm text-black">{{ carDetails.model }}</p>
                      </div>
                    </div>
                    <div class="grid grid-cols-4 gap-4">
                      <div class="mt-2">
                        <p class="text-sm text-gray-500">Year:</p>
                      </div>
                      <div class="mt-2">
                        <p class="text-sm text-black">{{ carDetails.year }}</p>
                      </div>
                    </div>
                  </div>
                  <div class="pb-3">
                    <div class="grid grid-cols-4 gap-4">
                      <div class="mt-2">
                        <p class="text-sm text-gray-500">Specifications</p>
                      </div>
                    </div>
                    <div class="grid grid-cols-4 gap-4">
                      <div class="mt-2">
                        <p class="text-sm text-gray-500">Engine:</p>
                      </div>
                      <div class="mt-2">
                        <p class="text-sm text-black">{{ specs.engine }}</p>
                      </div>
                      <div class="mt-2">
                        <p class="text-sm text-gray-500">Horsepower:</p>
                      </div>
                      <div class="mt-2">
                        <p class="text-sm text-black">{{ specs.horsepower }}</p>
                      </div>
                    </div>
                    <div class="grid grid-cols-4 gap-4">
                      <div class="mt-2">
                        <p class="text-sm text-gray-500">Torque:</p>
                      </div>
                      <div class="mt-2">
                        <p class="text-sm text-black">{{ specs.torque }}</p>
                      </div>
                      <div class="mt-2">
                        <p class="text-sm text-gray-500">Transmission:</p>
                      </div>
                      <div class="mt-2">
                        <p class="text-sm text-black">{{ specs.transmission }}</p>
                      </div>
                    </div>
                    <div class="grid grid-cols-4 gap-4">
                      <div class="mt-2">
                        <p class="text-sm text-gray-500">Drivetrain:</p>
                      </div>
                      <div class="mt-2">
                        <p class="text-sm text-black">{{ specs.drivetrain }}</p>
                      </div>
                      <div class="mt-2">
                        <p class="text-sm text-gray-500">Fuel Economy:</p>
                      </div>
                      <div class="mt-2">
                        <p class="text-sm text-black">{{ specs.fuelEconomy.combined }}</p>
                      </div>
                    </div>
                  </div>
                  <div class="pb-3">
                    <div class="grid grid-cols-4 gap-4">
                      <div class="mt-2">
                        <p class="text-sm text-gray-500">Dimensions</p>
                      </div>
                    </div>
                    <div class="grid grid-cols-4 gap-4">
                      <div class="mt-2">
                        <p class="text-sm text-gray-500">Wheelbase:</p>
                      </div>
                      <div class="mt-2">
                        <p class="text-sm text-black">{{ dimensions.wheelbase }}</p>
                      </div>
                      <div class="mt-2">
                        <p class="text-sm text-gray-500">Length:</p>
                      </div>
                      <div class="mt-2">
                        <p class="text-sm text-black">{{ dimensions.length }}</p>
                      </div>
                    </div>
                    <div class="grid grid-cols-4 gap-4">
                      <div class="mt-2">
                        <p class="text-sm text-gray-500">Width:</p>
                      </div>
                      <div class="mt-2">
                        <p class="text-sm text-black">{{ dimensions.width }}</p>
                      </div>
                      <div class="mt-2">
                        <p class="text-sm text-gray-500">Height:</p>
                      </div>
                      <div class="mt-2">
                        <p class="text-sm text-black">{{ dimensions.height }}</p>
                      </div>
                    </div>
                    <div class="grid grid-cols-4 gap-4">
                      <div class="mt-2">
                        <p class="text-sm text-gray-500">Curb Weight:</p>
                      </div>
                      <div class="mt-2">
                        <p class="text-sm text-black">{{ dimensions.curbWeight }}</p>
                      </div>
                    </div>
                  </div>
                  <div class="pb-3">
                    <div class="grid grid-cols-4 gap-4">
                      <div class="mt-2">
                        <p class="text-sm text-gray-500">Features</p>
                      </div>
                    </div>
                    <div class="my-3">
                      <div class="grid grid-cols-4 gap-4">
                        <div class="">
                          <p class="text-sm text-gray-500">Interior:</p>
                        </div>
                      </div>
                      <div class="grid grid-cols-2">
                        <div class="" v-for="interior in features.interior">
                          <p class="text-sm text-black">{{ interior }}</p>
                        </div>
                      </div>
                    </div>
                    <div class="my-3">
                      <div class="grid grid-cols-4 gap-4">
                        <div class="">
                          <p class="text-sm text-gray-500">Exterior:</p>
                        </div>
                      </div>
                      <div class="grid grid-cols-2">
                        <div class="" v-for="exterior in features.exterior">
                          <p class="text-sm text-black">{{ exterior }}</p>
                        </div>
                      </div>
                    </div>
                    <div class="mt-3">
                      <div class="grid grid-cols-4 gap-4">
                        <div class="mt-2">
                          <p class="text-sm text-gray-500">Safety:</p>
                        </div>
                      </div>
                      <div class="grid grid-cols-2">
                        <div class="" v-for="safety in features.safety">
                          <p class="text-sm text-black">{{ safety }}</p>
                        </div>
                      </div>
                    </div>
                  </div>
                  <div class="">
                    <div class="grid grid-cols-4 gap-4">
                      <div class="mt-2">
                        <p class="text-sm text-gray-500">Price</p>
                      </div>
                    </div>
                    <div class="grid grid-cols-4 gap-4">
                      <div class="mt-2">
                        <p class="text-sm text-gray-500">Destination Charge:</p>
                      </div>
                      <div class="mt-2">
                        <p class="text-sm text-black">{{ pricing.destinationCharge }}</p>
                      </div>
                      <div class="mt-2">
                        <p class="text-sm text-gray-500">Invoice:</p>
                      </div>
                      <div class="mt-2">
                        <p class="text-sm text-black">{{ pricing.invoice }}</p>
                      </div>
                    </div>
                    <div class="grid grid-cols-4 gap-4">
                      <div class="mt-2">
                        <p class="text-sm text-red-500">MSRP:</p>
                      </div>
                      <div class="mt-2">
                        <p class="text-sm text-red-500">{{ pricing.MSRP }}</p>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
            <!-- <div class="bg-gray-50 px-4 py-3 sm:flex sm:flex-row-reverse sm:px-6">
              <button
                @click="closeDialog"
                type="button"
                class="mt-3 inline-flex w-full justify-center rounded-md bg-white px-3 py-2 text-sm font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 hover:bg-gray-50 sm:mt-0 sm:w-auto"
              >
                Close
              </button>
            </div> -->
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      dimensions: {},
      specs: {},
      features: {},
      pricing: {}
    }
  },
  props: {
    openDialog: {
      type: Boolean,
      default: false,
      required: true
    },
    carDetails: {
      type: Object,
      default: () => ({}),
      required: true
    }
  },
  methods: {
    closeDialog() {
      this.$emit('closeDialog')
    }
  },
  watch: {
    carDetails: {
      immediate: true,
      handler(newVal) {
        this.dimensions = newVal.dimensions || {}
        this.specs = newVal.specs || {}
        this.features = newVal.features || {}
        this.pricing = newVal.pricing || {}
      }
    }
  }
}
</script>
