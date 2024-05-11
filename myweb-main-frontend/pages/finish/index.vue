<template>
    <title>TAKAHATA</title>
    <h1>Finish</h1>
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
</template>