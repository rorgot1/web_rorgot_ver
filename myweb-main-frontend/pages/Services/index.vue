<template>
  <div>
    <!-- Header -->
    <header class="box-content h-8 w-50 p-4 border-4 bg-Slate-50">
      <div class="flex items-center justify-between">
        <a href="#" class="-m-1.5 p-1.5">
          <img class="h-8 w-auto" src="/image/ex.png" alt="" />
        </a>
        <div class="flex items-center space-x-2">
          <router-link to="/home/">
            <button class="rounded-full bg-gray-200 text-gray-800 px-4 py-2">Home</button>
          </router-link>
          <a href="https://sites.google.com/view/takahata" target="_blank">
            <button class="rounded-full bg-gray-200 text-gray-800 px-4 py-2">Shuttle booking</button>
          </a>
          <button class="rounded-full bg-gray-200 text-gray-800 px-4 py-2">Notification</button>
          <router-link to="/">
            <button class="rounded-full bg-green-500 text-white px-4 py-2">Logout</button>
          </router-link>
        </div>
      </div>
    </header>

    <!-- Main Content -->
    <main class="container mx-auto py-10 bg-Teal-600">
      <div class="text-center mb-8">
        <h2 class="text-2xl font-semibold">ระบบแจ้งซ่อม</h2>
      </div>

      <!-- Form -->
      <form class="mx-auto max-w-lg">
        <div class="mb-4">
          <label for="selectTopic" class="block mb-2">เลือกเรื่อง</label>
          <select name="topic" id="selectTopic" class="form-select" v-model="selectedTopic" @change="loadIssues" required>
           <!-- <option value="" disabled hidden selected>{{ selectedTopic ? selectedTopic : 'Please select item' }}</option>-->
            <option v-for="i in ty1" :key="i.id" :value="i.name">{{ i.name }}</option>
          </select>
        </div>

        <!-- Select Issue -->
        <div class="mb-4" v-if="ty2.length > 0"> 
          <label for="selectIssue" class="block mb-2">เลือกหัวข้อ</label>
          <select name="issue" id="selectIssue" class="form-select" v-model="selectedIssue" @change="console.log(selectedIssue)" required>
           <!-- <option value="" disabled hidden selected>{{ selectedIssue ? selectedIssue : 'Please select item' }}</option>-->
            <option v-for="j in ty2" :key="j.id">{{ j.name }}</option>
          </select>
        </div>

        <!-- Explanation -->
        <div class="mb-4">
          <label  for="explanation" class="block mb-2">Description</label>
          <textarea id="explanation" class="h-32 w-full border rounded-lg px-4" rows="3" v-model="reason" required></textarea>
        </div>

        <!-- Buttons -->
        <div class="flex items-center justify-center space-x-2 flex-grow">

          <button @click="save_button" class="rounded-full bg-green-500 text-white px-4 py-2">Save</button>

        <router-link to="/home/">
          <button class="rounded-full bg-red-600 text-white px-4 py-2">Cancel</button>
        </router-link>
        </div>
      </form>
    </main>
  </div>
</template>

<script setup>


  const ty1 = ref([]);
  const ty2 = ref([]); 
  const selectedTopic = ref();
  const selectedIssue = ref();
  const reason = ref();

  const fetchData = async () => {
    try {
      const response = await $fetch('http://localhost:5100/api/get/typeRepair', { credentials: 'include' });
      ty1.value = response.results;
    } catch (error) {
      console.error('Failed to fetch ty1 data:', error);
    }
  };

  const loadIssues = async () => {
    try {
      if (selectedTopic.value) {
        const response = await $fetch('http://localhost:5100/api/get/resource', { 
          method : "POST",
          body:{
            type : selectedTopic.value,
          },
          credentials: 'include' });
          ty2.value = response.results;
      }
    } catch (error) {
      console.error('Failed to fetch ty2 data:', error);
    }
  };

  const save_button = async () => {
    try{
      console.log(selectedTopic.value);
      console.log(selectedIssue.value);
      console.log(reason.value);      
      console.log()

    }catch (error){
      console.error('Failed to go finish page:', error);
    }

  } 

  fetchData();
</script>


<style scoped>
/* Add any scoped styles here */
</style>
