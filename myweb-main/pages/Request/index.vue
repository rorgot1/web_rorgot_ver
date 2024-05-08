<template>
  <title>TAKAHATA</title>
  <div>
    <!-- Header -->
    <header class="box-content h-8 w-50 p-4 border-4 bg-Slate-50">
      <div class="flex items-center justify-between">
        <a href="#" class="-m-1.5 p-1.5">
          <img class="h-8 w-auto" src="/image/ex.png" alt="" />
        </a>
        <div class="flex items-center space-x-2">
          <router-link to="/">
            <button class="rounded-full bg-gray-200 text-gray-800 px-4 py-2">Home</button>
          </router-link>
          <a href="https://sites.google.com/view/takahata" target="_blank">
            <button class="rounded-full bg-gray-200 text-gray-800 px-4 py-2">Shuttle booking</button>
          </a>
          <button class="rounded-full bg-gray-200 text-gray-800 px-4 py-2">Notification</button>
          <router-link to="/login/">
            <button class="rounded-full bg-green-500 text-white px-4 py-2">Logout</button>
          </router-link>
        </div>
      </div>
    </header>

    <!-- Main Content -->
    <main class="container mx-auto py-10 bg-Teal-600">
      <div class="text-center mb-8">
        <h2 class="text-2xl font-semibold">Request</h2>
      </div>
      
      <div class="flex flex-col">
        <!-- Column 1 -->
        <div class="border rounded-md p-4 mb-4">
          <fieldset>
            <legend class="text-sm font-semibold leading-6 text-gray-900">User Account</legend>
            <div class="mt-6 space-y-6">
              <div class="flex items-center gap-x-3">
                <input id="push-everything1" name="push-notifications1" type="radio" class="h-4 w-4 border-gray-300 text-indigo-600 focus:ring-indigo-600" />
                <label for="push-everything1" class="block text-sm font-medium leading-6 text-gray-900">User Login </label>
              </div>
              <div class="flex items-center gap-x-3">
                <input id="push-email1" name="push-notifications1" type="radio" class="h-4 w-4 border-gray-300 text-indigo-600 focus:ring-indigo-600" />
                <label for="push-email1" class="block text-sm font-medium leading-6 text-gray-900">User E-mail </label>
              </div>
              <div class="flex items-center gap-x-3">
                <input id="push-nothing1" name="push-notifications1" type="radio" class="h-4 w-4 border-gray-300 text-indigo-600 focus:ring-indigo-600" />
                <label for="push-nothing1" class="block text-sm font-medium leading-6 text-gray-900">User Internet</label>
              </div>
              <div class="flex items-center gap-x-3">
                <input id="push-ERP&MRP1" name="push-notifications1" type="radio" class="h-4 w-4 border-gray-300 text-indigo-600 focus:ring-indigo-600" />
                <label for="push-ERP&MRP1" class="block text-sm font-medium leading-6 text-gray-900">User ERP&MRP</label>
              </div>
              <div class="mt-10 grid grid-cols-1 gap-x-6 gap-y-8 sm:grid-cols-6">
                <div class="sm:col-span-4">
                  <label for="username" class="block text-sm font-medium leading-6 text-gray-900">Username</label>
                  <div class="mt-2">
                    <div class="flex rounded-md shadow-sm ring-1 ring-inset ring-gray-300 focus-within:ring-2 focus-within:ring-inset focus-within:ring-indigo-600 sm:max-w-md">
                      
                      <input type="text" name="username" id="username" autocomplete="username" class="block flex-1 border-0 bg-transparent py-1.5 pl-1 text-gray-900 placeholder:text-gray-400 focus:ring-0 sm:text-sm sm:leading-6" placeholder="janesmith" />
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </fieldset>
        </div>

        <!-- Column 2 -->
        <div class="border rounded-md p-4 mb-4">
          <fieldset>
            <legend class="text-sm font-semibold leading-6 text-gray-900">Hardware </legend>
            <div class="mt-6 space-y-6">
              <div class="flex items-center gap-x-3">
                <input id="Desktop2" name="push-notifications2" type="radio" class="h-4 w-4 border-gray-300 text-indigo-600 focus:ring-indigo-600" />
                <label for="Desktop2" class="block text-sm font-medium leading-6 text-gray-900">Desktop PC</label>
              </div>
              <div class="flex items-center gap-x-3">
                <input id="Notebook2" name="push-notifications2" type="radio" class="h-4 w-4 border-gray-300 text-indigo-600 focus:ring-indigo-600" />
                <label for="Notebook2" class="block text-sm font-medium leading-6 text-gray-900">Notebook </label>
              </div>
              <div class="flex items-center gap-x-3">
                <input id="Printer2" name="push-notifications2" type="radio" class="h-4 w-4 border-gray-300 text-indigo-600 focus:ring-indigo-600" />
                <label for="Printer2" class="block text-sm font-medium leading-6 text-gray-900">Printer </label>
              </div>
            </div>
            <div class="mt-6 space-y-6">
              <div class="flex items-center gap-x-3">
                <input id="Barcode Scanne2" name="push-notifications2" type="radio" class="h-4 w-4 border-gray-300 text-indigo-600 focus:ring-indigo-600" />
                <label for="Barcode Scanne2" class="block text-sm font-medium leading-6 text-gray-900">Barcode Scanner</label>
              </div>
              <div class="flex items-center gap-x-3">
                <input id="CCTV2" name="push-notifications2" type="radio" class="h-4 w-4 border-gray-300 text-indigo-600 focus:ring-indigo-600" />
                <label for="CCTV2" class="block text-sm font-medium leading-6 text-gray-900">CCTV </label>
              </div>
              <div class="flex items-center gap-x-3">
                <input id="Smartphone&Table2" name="push-notifications2" type="radio" class="h-4 w-4 border-gray-300 text-indigo-600 focus:ring-indigo-600" />
                <label for="Smartphone&Table2" class="block text-sm font-medium leading-6 text-gray-900">Smartphone&Tablet</label>
              </div>
              <div class="flex items-center gap-x-3">
                <input id="Other2" name="push-notifications2" type="radio" class="h-4 w-4 border-gray-300 text-indigo-600 focus:ring-indigo-600" />
                <label for="Other2" class="block text-sm font-medium leading-6 text-gray-900">Other</label>
              </div>
            </div>
          </fieldset>
        </div>

        <!-- Column 3 -->
        <div class="border rounded-md p-4 mb-4">
          <fieldset>
            <legend class="text-sm font-semibold leading-6 text-gray-900">Software License</legend>
            <div class="mt-6 space-y-6">
              <div class="flex items-center gap-x-3">
                <input id="Microsoft Office 3" name="push-notifications3" type="radio" class="h-4 w-4 border-gray-300 text-indigo-600 focus:ring-indigo-600" />
                <label for="Microsoft Office 3" class="block text-sm font-medium leading-6 text-gray-900">Microsoft Office </label>
              </div>
              <div class="flex items-center gap-x-3">
                <input id="AutoCAD3" name="push-notifications3" type="radio" class="h-4 w-4 border-gray-300 text-indigo-600 focus:ring-indigo-600" />
                <label for="AutoCAD3" class="block text-sm font-medium leading-6 text-gray-900">AutoCAD</label>
              </div>
              <div class="flex items-center gap-x-3">
                <input id="Jancom (ACC)3" name="push-notifications3" type="radio" class="h-4 w-4 border-gray-300 text-indigo-600 focus:ring-indigo-600" />
                <label for="Jancom (ACC)3" class="block text-sm font-medium leading-6 text-gray-900">Jancom (ACC)</label>
              </div>
              <div class="flex items-center gap-x-3">
                <input id="Tiger HER (HRD)3" name="push-notifications3" type="radio" class="h-4 w-4 border-gray-300 text-indigo-600 focus:ring-indigo-600" />
                <label for="Tiger HER (HRD)3" class="block text-sm font-medium leading-6 text-gray-900">Tiger HER (HRD)</label>
              </div>
              <div class="flex items-center gap-x-3">
                <input id="Other3" name="push-notifications3" type="radio" class="h-4 w-4 border-gray-300 text-indigo-600 focus:ring-indigo-600" />
                <label for="Other3" class="block text-sm font-medium leading-6 text-gray-900">Other</label>
              </div>
            </div>
          </fieldset>
        </div>
        <!-- Column 4 -->
        <div class="border rounded-md p-4 mb-4">
          <fieldset>
            <legend class="text-sm font-semibold leading-6 text-gray-900">ERP&MRP</legend>
            <div class="mt-6 space-y-6">
              <div class="flex items-center gap-x-3">
                <input id="Real-Time4" name="push-notifications1" type="radio" class="h-4 w-4 border-gray-300 text-indigo-600 focus:ring-indigo-600" />
                <label for="Real-Time4" class="block text-sm font-medium leading-6 text-gray-900">Real-Time</label>
              </div>
              <div class="flex items-center gap-x-3">
                <input id="DCS4" name="push-notifications1" type="radio" class="h-4 w-4 border-gray-300 text-indigo-600 focus:ring-indigo-600" />
                <label for="DCS4" class="block text-sm font-medium leading-6 text-gray-900">DCS</label>
              </div>
              <div class="flex items-center gap-x-3">
                <input id="FOXPRO4" name="push-notifications1" type="radio" class="h-4 w-4 border-gray-300 text-indigo-600 focus:ring-indigo-600" />
                <label for="FOXPRO4" class="block text-sm font-medium leading-6 text-gray-900">FOXPRO</label>
              </div>
            </div>
          </fieldset>
        </div>

        <!-- Column 5 -->
        <div class="border rounded-md p-4 mb-4">
          <fieldset>
            <legend class="text-sm font-semibold leading-6 text-gray-900">PFile Server </legend>
            <div class="mt-6 space-y-6">
              <div class="flex items-center gap-x-3">
                <input id="Folder5" name="push-notifications2" type="radio" class="h-4 w-4 border-gray-300 text-indigo-600 focus:ring-indigo-600" />
                <label for="Folder5" class="block text-sm font-medium leading-6 text-gray-900">Folder</label>
              </div>
              <div class="flex items-center gap-x-3">
                <input id="Authentication5" name="push-notifications2" type="radio" class="h-4 w-4 border-gray-300 text-indigo-600 focus:ring-indigo-600" />
                <label for="Authentication5" class="block text-sm font-medium leading-6 text-gray-900">Authentication </label>
              </div>
              <div class="flex items-center gap-x-3">
                <input id="Quota5" name="push-notifications2" type="radio" class="h-4 w-4 border-gray-300 text-indigo-600 focus:ring-indigo-600" />
                <label for="Quota5" class="block text-sm font-medium leading-6 text-gray-900">Quota</label>
              </div>
              <div class="flex items-center gap-x-3">
                <input id="Restore Data5" name="push-notifications2" type="radio" class="h-4 w-4 border-gray-300 text-indigo-600 focus:ring-indigo-600" />
                <label for="Restore Data5" class="block text-sm font-medium leading-6 text-gray-900">Restore Data</label>
              </div>
            </div>
          </fieldset>
        </div>

        <!-- Column 6 -->
        <div class="border rounded-md p-4 mb-4">
          <fieldset>
            <legend class="text-sm font-semibold leading-6 text-gray-900">Installation</legend>
            <div class="mt-6 space-y-6">
              <div class="flex items-center gap-x-3">
                <input id="Wire Network 6" name="push-notifications3" type="radio" class="h-4 w-4 border-gray-300 text-indigo-600 focus:ring-indigo-600" />
                <label for="Wire Network 6" class="block text-sm font-medium leading-6 text-gray-900">Wire Network (LAN)</label>
              </div>
              <div class="flex items-center gap-x-3">
                <input id="Wireless6" name="push-notifications3" type="radio" class="h-4 w-4 border-gray-300 text-indigo-600 focus:ring-indigo-600" />
                <label for="Wireless6" class="block text-sm font-medium leading-6 text-gray-900">Wireless ( WiFi)</label>
              </div>
              <div class="flex items-center gap-x-3">
                <input id="Internet6" name="push-notifications3" type="radio" class="h-4 w-4 border-gray-300 text-indigo-600 focus:ring-indigo-600" />
                <label for="Internet 6" class="block text-sm font-medium leading-6 text-gray-900">Internet </label>
              </div>
              <div class="flex items-center gap-x-3">
                <input id="VPN 6" name="push-notifications3" type="radio" class="h-4 w-4 border-gray-300 text-indigo-600 focus:ring-indigo-600" />
                <label for="VPN 6" class="block text-sm font-medium leading-6 text-gray-900">VPN </label>
              </div>
              <div class="flex items-center gap-x-3">
                <input id="Telephone6" name="push-notifications3" type="radio" class="h-4 w-4 border-gray-300 text-indigo-600 focus:ring-indigo-600" />
                <label for="Telephone 6" class="block text-sm font-medium leading-6 text-gray-900">Telephone </label>
              </div>
            </div>
          </fieldset>
        </div>
      </div>

      <!-- Explanation -->
      <div class="mb-4">
        <label for="explanation" class="block mb-2">อธิบาย</label>
        <textarea id="explanation" class="form-control h-32 w-full border rounded-lg px-4" rows="3" v-model="explanation" required></textarea>
      </div>

      <!-- Buttons -->
      <div class="flex items-center justify-center space-x-2 flex-grow">
        <button class="rounded-full bg-green-500 text-white px-4 py-2" @click="save">Save</button>
        <button class="rounded-full bg-yellow-500 text-white px-4 py-2" @click="reset">Reset</button>
        <button class="rounded-full bg-red-600 text-white px-4 py-2" @click="cancel">Cancel</button>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  data() {
    return {
      pushNotification: '', // Selected push notification option
      explanation: '' // Textarea value
    };
  },
  methods: {
    save() {
      // Save functionality
    },
    reset() {
      // Reset functionality
    },
    cancel() {
      // Cancel functionality
    }
  }
};
</script>

<style scoped>
/* Add any scoped styles here */
</style>
