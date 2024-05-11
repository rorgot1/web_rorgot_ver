<template>
  <title>TAKAHATA</title>
  <div>
    <!-- Box content with text -->
    <header class="box-content h-8 w-50 p-4 border-4 bg-Slate-50">
      <div class="flex items-center justify-between">
        <a href="#" class="-m-1.5 p-1.5">
          <img class="h-8 w-auto" src="/image/ex.png" alt="" />
        </a>
        <div class="flex items-center space-x-2">
          <a href="https://sites.google.com/view/takahata" target="_blank">
            <button class="rounded-full bg-gray-200 text-gray-800 px-4 py-2">
              Shuttle booking
            </button>
          </a>
          <router-link to="/Notification/">
          <button class="rounded-full bg-gray-200 text-gray-800 px-4 py-2">
            Notification
          </button>
        </router-link>
          <router-link to="/">
            <button class="rounded-full bg-green-500 text-white px-4 py-2">
              Logout
            </button>
          </router-link>
        </div>
      </div>
    </header>

    <div class="box-content h-96 w-100 p-4 border-4 bg-sky-300"></div>
    <div>
      <div class="grid grid-cols-2 gap-4">
        <!-- Column 1 -->
        <div
          class="border border-gray-400 p-4 flex flex-col justify-center items-center"
        >
          <h2 class="text-lg font-semibold mb-4">IT Request</h2>
          <!-- Content for column 1 -->
          <router-link to="/Request/">
            <button class="rounded-full bg-blue-500 text-white px-4 py-2">
              Click here
            </button>
          </router-link>
        </div>

        <!-- Column 2 -->
        <div
          class="border border-gray-400 p-4 flex flex-col justify-center items-center"
        >
          <h2 class="text-lg font-semibold mb-4">IT Services</h2>
          <!-- Content for column 2 -->
          <router-link to="/Services/">
            <button class="rounded-full bg-blue-500 text-white px-4 py-2">
              Click here
            </button>
          </router-link>
        </div>
      </div>
    </div>
  </div>
</template>
