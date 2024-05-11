<template>
  <title>TAKAHATA</title>

  <!-- Box content with text -->
  <header class="box-content h-8 w-50 p-4 bg-Slate-50">
      <div class="flex items-center justify-between">
          <a href="#" class="-m-1.5 p-1.5">
              <img class="h-8 w-auto" src="/image/ex.png" alt="" />
          </a>

          <div class="flex items-center space-x-2">
              <div class="inline-block align-middle mx-auto max-w-md ">
                  <h1> Kunanya Srinongnuch </h1>
              </div>
              <router-link to="/home/">
                  <button class="rounded-full bg-gray-200 text-gray-800 px-4 py-2">
                      Home
                  </button>
              </router-link>
              <a href="https://sites.google.com/view/takahata" target="_blank">
                  <button class="rounded-full bg-gray-200 text-gray-800 px-4 py-2">
                      Shuttle booking
                  </button>
              </a>
              <button class="rounded-full bg-gray-200 text-gray-800 px-4 py-2">
                  Notification
              </button>
              <router-link to="/">
                  <button class="rounded-full bg-green-500 text-white px-4 py-2">
                      Logout
                  </button>
              </router-link>
          </div>
      </div>
  </header>
  <!-- ผลสรุปของข้อมูล -->
  <div class=" box-content  p-4 bg-sky-500 ">
      <div>
          <div class="bg-white py-24 sm:py-32 ">
              <div class="mx-auto max-w-7xl px-6 lg:px-8 ">
                  <dl class="grid grid-cols-1 gap-x-8 gap-y-16 text-center lg:grid-cols-3">
                      <div v-for="stat in stats" :key="stat.id" class="mx-auto flex max-w-xs flex-col gap-y-4">
                          <dt class="text-base leading-7 text-gray-600">{{ stat.name }}</dt>
                          <dd class="order-first text-3xl font-semibold tracking-tight text-gray-900 sm:text-5xl">{{
                              stat.value }}
                          </dd>
                      </div>
                  </dl>
              </div>
          </div>
      </div>
  </div>

  <div class="mt-10 box-border text-xl font-semibold  bg-Slate-950 ">
      <main class=" box-border text-xl font-semibold  bg-Slate-50 ">
          <div class="text-center mb-8">
              <h2 class="  text-2xl font-semibold ">IT Service</h2>
          </div>
          <div class="box-border text-xl font-semibold h-8 w-50 p-4 ">
              <div class="">

                  <div>
                      <label class="relative block">
                          <span class="sr-only">Search</span>
                          <span class="absolute inset-y-0 left-0 flex items-center pl-2">
                              <svg class="h-5 w-5 fill-slate-300" viewBox="0 0 20 20"><!-- ... --></svg>
                          </span>
                          <input
                              class="placeholder:italic placeholder:text-slate-400 block bg-white  border border-slate-300 rounded-md py-2 pl-9 pr-3 shadow-sm focus:outline-none focus:border-sky-500 focus:ring-sky-500 focus:ring-1 sm:text-sm"
                              placeholder="Search for anything..." type="text" name="search" />
                      </label>
                  </div>
              </div>
              <diV class="mt-3">
                  <div class="overflow-x-auto">
                      <table class="table ">
                          <thead>
                              <tr>
                                  <th>Job No</th>
                                  <th>EN</th>
                                  <th>Requester</th>
                                  <th>Section</th>
                                  <th>Tel</th>
                                  <th>Device Type</th>
                                  <th>Create Date</th>
                                  <th>Subject</th>
                                  <th>Status</th>
                                  <th>Detail</th>

                              </tr>
                          </thead>
                          <tbody>
                              <tr v-for="item in items" :key="item.Job_No">
                                  <td>{{ item.job_No }}</td>
                                  <td>{{ item.en }}</td>
                                  <td>{{ item.tel }}</td>
                                  <td>{{ item.requester }}</td>
                                  <td>{{ item.section }}</td>
                                  <td>{{ item.device_type }}</td>
                                  <td>{{ item.create_date }}</td>
                                  <td>{{ item.subject }}</td>
                                  <td>{{ item.status }}</td>
                                  <td>{{ item.detail }}</td>
                              </tr>
                          </tbody>
                      </table>
                  </div>
                  <div class="flex items-center justify-between border-t border-gray-200 bg-white px-4 py-3 sm:px-6">
                      <div class="flex flex-1 justify-between sm:hidden">
                          <a href="#"
                              class="relative inline-flex items-center rounded-md border border-gray-300 bg-white px-4 py-2 text-sm font-medium text-gray-700 hover:bg-gray-50">Previous</a>
                          <a href="#"
                              class="relative ml-3 inline-flex items-center rounded-md border border-gray-300 bg-white px-4 py-2 text-sm font-medium text-gray-700 hover:bg-gray-50">Next</a>
                      </div>
                      
                      <div class="hidden sm:flex sm:flex-1 sm:items-center sm:justify-between">
                          <div>
                              <p class="text-sm text-gray-700">
                                  Showing
                                  {{ ' ' }}
                                  <span class="font-medium">1</span>
                                  {{ ' ' }}
                                  to
                                  {{ ' ' }}
                                  <span class="font-medium">10</span>
                                  {{ ' ' }}
                                  of
                                  {{ ' ' }}
                                  <span class="font-medium">97</span>
                                  {{ ' ' }}
                                  results
                              </p>
                          </div>

                          <div>
                              <nav class="isolate inline-flex -space-x-px rounded-md shadow-sm"
                                  aria-label="Pagination">
                                  <a href="#"
                                      class="relative inline-flex items-center rounded-l-md px-2 py-2 text-gray-400 ring-1 ring-inset ring-gray-300 hover:bg-gray-50 focus:z-20 focus:outline-offset-0">
                                      <span class="sr-only">Previous</span>
                                      <ChevronLeftIcon class="h-5 w-5" aria-hidden="true" />
                                  </a>
                                  <!-- Current: "z-10 bg-indigo-600 text-white focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600", Default: "text-gray-900 ring-1 ring-inset ring-gray-300 hover:bg-gray-50 focus:outline-offset-0" -->
                                  <a href="#" aria-current="page"
                                      class="relative z-10 inline-flex items-center bg-indigo-600 px-4 py-2 text-sm font-semibold text-white focus:z-20 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600">1</a>
                                  <a href="#"
                                      class="relative inline-flex items-center px-4 py-2 text-sm font-semibold text-gray-900 ring-1 ring-inset ring-gray-300 hover:bg-gray-50 focus:z-20 focus:outline-offset-0">2</a>
                                  <a href="#"
                                      class="relative hidden items-center px-4 py-2 text-sm font-semibold text-gray-900 ring-1 ring-inset ring-gray-300 hover:bg-gray-50 focus:z-20 focus:outline-offset-0 md:inline-flex">3</a>
                                  <span
                                      class="relative inline-flex items-center px-4 py-2 text-sm font-semibold text-gray-700 ring-1 ring-inset ring-gray-300 focus:outline-offset-0">...</span>
                                  <a href="#"
                                      class="relative hidden items-center px-4 py-2 text-sm font-semibold text-gray-900 ring-1 ring-inset ring-gray-300 hover:bg-gray-50 focus:z-20 focus:outline-offset-0 md:inline-flex">8</a>
                                  <a href="#"
                                      class="relative inline-flex items-center px-4 py-2 text-sm font-semibold text-gray-900 ring-1 ring-inset ring-gray-300 hover:bg-gray-50 focus:z-20 focus:outline-offset-0">9</a>
                                  <a href="#"
                                      class="relative inline-flex items-center px-4 py-2 text-sm font-semibold text-gray-900 ring-1 ring-inset ring-gray-300 hover:bg-gray-50 focus:z-20 focus:outline-offset-0">10</a>
                                  <a href="#"
                                      class="relative inline-flex items-center rounded-r-md px-2 py-2 text-gray-400 ring-1 ring-inset ring-gray-300 hover:bg-gray-50 focus:z-20 focus:outline-offset-0">
                                      <span class="sr-only">Next</span>
                                      <ChevronRightIcon class="h-5 w-5" aria-hidden="true" />
                                  </a>
                              </nav>

                          </div>
                      </div>
                  </div>


              </diV>
          </div>


      </main>

  </div>




</template>

<script>
export default {
  data() {
      return {
          items: [
              { job_No: "2024-r-0001", en: 10106, requester: 'kunanya s.', section: 'EDP', tel: '056', device_type: 'Computer', create_date: '12/05/2567 23:50', subject: 'Keyboard', status: 'open', detail: 'button', },
              { job_No: "2024-r-0001", en: 10106, requester: 'kunanya s.', section: 'EDP', tel: '056', device_type: 'Computer', create_date: '12/05/2567 23:50', subject: 'Keyboard', status: 'open', detail: 'button', },
              { job_No: "2024-r-0001", en: 10106, requester: 'kunanya s.', section: 'EDP', tel: '056', device_type: 'Computer', create_date: '12/05/2567 23:50', subject: 'Keyboard', status: 'open', detail: 'button', },
              { job_No: "2024-r-0001", en: 10106, requester: 'kunanya s.', section: 'EDP', tel: '056', device_type: 'Computer', create_date: '12/05/2567 23:50', subject: 'Keyboard', status: 'open', detail: 'button', },

              // Add more sample data objects here
          ]
      };
  }
};
</script>

<style>
.table {
  width: 100%;
  border-collapse: collapse;
}

.table th,
.table td {
  border: 1px solid #ccc;
  padding: 8px;
  text-align: left;
}
</style>
<script setup>
const stats = [
  { id: 1, name: ' REMEDIATION WORK ORDER', value: '44 ' },
  { id: 2, name: 'MANUFACTURING WORK ORDER', value: '23' },
  { id: 3, name: 'SUM UP', value: '67' },
]
</script>