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
          <select name="topic" id="selectTopic" class="form-select" v-model="selectedTopic" @change="loadIssues"
            required>
            <!-- <option value="" disabled hidden selected>{{ selectedTopic ? selectedTopic : 'Please select item' }}</option>-->
            <option v-for="i in ty1" :key="i.id" :value="i.name">{{ i.name }}</option>
          </select>
        </div>

        <!-- Select Issue -->
        <div class="mb-4" v-if="ty2.length > 0">
          <label for="selectIssue" class="block mb-2">เลือกหัวข้อ</label>
          <select name="issue" id="selectIssue" class="form-select" v-model="selectedIssue" required>
            <!-- <option value="" disabled hidden selected>{{ selectedIssue ? selectedIssue : 'Please select item' }}</option>-->
            <option v-for="j in ty2" :key="j.id">{{ j.name }}</option>
          </select>
        </div>

        <!-- Explanation -->
        <div class="mb-4">
          <label for="explanation" class="block mb-2">Description</label>
          <textarea id="explanation" class="h-32 w-full border rounded-lg px-4" rows="3" v-model="reason"
            required></textarea>
        </div>
      </form>
      <!-- Buttons -->
      <div class="flex items-center justify-center space-x-2 flex-grow">
        <button @click="save_button" class="rounded-full bg-green-500 text-white px-4 py-2">Save</button>
        <router-link to="/home/">
          <button class="rounded-full bg-red-600 text-white px-4 py-2">Cancel</button>
        </router-link>
        <button @click="admin_IT_check" class="rounded-full bg-yellow-500 text-admin px-4 py-2">Admin</button>
      </div>
    </main>
  </div>
</template>

<script setup>
const ty1 = ref([]);
const ty2 = ref([]);
const selectedTopic = ref();
const selectedIssue = ref();
const reason = ref();
import { jwtDecode } from "jwt-decode";
const token = jwtDecode(useCookie("token").value) //nuxt cookie & jwtDecode nuxt

const fetchData = async () => {
  try {
    const response = await $fetch('http://localhost:5600/api/get/typeRepair', { credentials: 'include' });
    ty1.value = response.results;
  } catch (error) {
    console.error('Failed to fetch Topic type data:', error);
  }
};
//
const loadIssues = async () => {
  try {
    if (selectedTopic.value) {
      const response = await $fetch('http://localhost:5600/api/get/resource', {
        method: "POST",
        body: {
          type: selectedTopic.value,
        },
        credentials: 'include'
      });
      ty2.value = response.results;
    }
  } catch (error) {
    console.error('Failed to fetch ty2 data:', error);
  }
};
//{en, name, section_id, tel, type, resource, detail}
const save_button = async () => {
  try {
      const response = await $fetch('http://localhost:5600/api/IT_Repair_data', {
        method: "POST",
        body: {
          en: token.userId,
          name: token.name,
          section_id: token.department,
          tel: token.tel,
          type: selectedTopic.value,
          resource: selectedIssue.value,
          detail: reason.value,
          status : "Wait"
        },credentials: 'include'      
      });
      //console.log(token.role)
    /*console.log(token.userId)
    console.log(token.name);
    console.log(token.department);
    console.log(token.tel);
    console.log(selectedTopic.value);
    console.log(selectedIssue.value);
    console.log(reason.value);*/

  } catch (error) {
    console.error('Failed to save data:', error);
  }

};

const admin_IT_check = async () =>{
  try{
      if (token.role == 3){
        navigateTo('/adminITcheck')
      } else{
        console.log("You are not Admin.")
      }
  } catch (error){
    console.error('Failed to check role :', error);
  }

};


fetchData();


</script>


<style scoped>
/* Add any scoped styles here */
</style>
