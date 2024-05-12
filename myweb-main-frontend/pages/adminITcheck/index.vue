<template>
  <div>
    <table class="table">
      <thead>
        <tr>
          <th style="width: 7.5%;">Job No.</th>
          <th style="width: 2%;">EN</th>
          <th style="width: 15%;">Requester</th>
          <th style="width: 3%;">Section</th>
          <th style="width: 5%;">Tel.</th>
          <th style="width: 11.5%;">Create date</th>
          <th style="width: 9.2%;">Type</th>
          <th style="width: 11.3%;">Device</th>
          <th style="width: 15%;">Detail</th>
          <th style="width: 15%;">Status</th>
          <th style="width: 10%;">Export</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in meme" :key="index">
          <td>{{ item.job_no }}</td>
          <td>{{ item.en }}</td>
          <td>{{ item.requester }}</td>
          <td>{{ item.department }}</td>
          <td>{{ item.tel }}</td>
          <td>{{ item.create_date }}</td>
          <td>{{ item.type }}</td>
          <td>{{ item.resource }}</td>
          <td> 
            <!--Pop up-->
            <div>
              <span v-if="isTextTruncated(item.reason)">
                {{ truncateText(item.reason, 18.5) }}
                <span class="more-link" @click="showFullText(item.reason)">more</span>
              </span>
              <span v-else>
                {{ item.reason }}
              </span>
            </div>
          </td>
          <td>
            <div class="status-cell">
              <span v-if="item.editing !== index" :style="{ color: getStatusColor(item.status) }">{{ item.status
                }}</span>
              <div v-else class="custom-dropdown">
                <select v-model="item.updatedStatus" class="dropdown-menu">
                  <option value="Wait" :style="{ color: 'black' }">Wait</option>
                  <option value="Open" :style="{ color: 'green' }">Open</option>
                  <option value="Close" :style="{ color: 'red' }">Close</option>
                  <option value="In Process" :style="{ color: 'orange' }">In Process</option>
                </select>

                <div class="dropdown-arrow"></div>
              </div>
              <button @click="editStatus(index)" class="edit-button">Edit</button>
              <div v-if="item.editing === index" class="action-buttons">
                <button @click="applyEdit(index)" class="apply-button" style="background-color: green;">Apply</button>
                <button @click="cancelEdit(index)" class="cancel-button" style="background-color: red;">Cancel</button>
              </div>
            </div>
          </td>
          <td>
            <!-- Placeholder for Export button -->
            <div style="text-align: center;">
              <button onclick="" class="pdf-button" style="text-decoration: underline; font-size: 14px;">PDF</button>
            </div>

          </td>
        </tr>
      </tbody>
    </table>

    <!-- Modal for Full Text -->
    <div class="modal" v-if="showModal">
      <div class="modal-content">
        <span class="close" @click="closeModal">&times;</span>
        <div class="full-text">
          {{ selectedReason }}
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
const meme = ref([]);
const State = ref();
const item = ref();

const test_data = async () => {

  try {
    const response = await fetch('http://localhost:5600/api/IT_Repair_data_table', {
      method: "POST",
      credentials: 'include'
    });
    const data = await response.json();
    meme.value = data.results;
  } catch (error) {
    console.error('Failed to fetch data:', error);
  }
};
test_data();

const status_update = async (index) => {
  try {
    const response = await $fetch('http://localhost:5600/api/IT_Repair_status_choice', {
      method: "POST",
      body: {
        data: meme.value[index].status,
        job_no: meme.value[index].job_no
      }, credentials: 'include'
    })
    State.value = response.results
    console.log(State.value)

  } catch (error) {
    console.error('Failed to fetch test_api data:', error);
  }
}
//editStatus(index)
const truncateText = (text, maxLength) => {
  if (text && text.length > maxLength) {
    return text.slice(0, maxLength) + '...';
  }
  return text;
};

const isTextTruncated = (text) => {
  return text && text.length > 25; // Check if text exceeds 25 characters
};

let showModal = ref(false);
let selectedReason = ref('');

const showFullText = (reason) => {
  selectedReason.value = reason;
  showModal.value = true;
};

const closeModal = () => {
  showModal.value = false;
};

const getStatusColor = (status) => {
  switch (status) {
    case 'Wait':
      return 'black';
    case 'Open':
      return 'green';
    case 'Close':
      return 'red';
    case 'In Process':
      return 'orange';
    default:
      return 'black';
  }
};



const editStatus = (index) => {
  meme.value[index].editing = index;
  meme.value[index].updatedStatus = meme.value[index].status;
};
const cancelEdit = (index) => {
  meme.value[index].editing = -1; // Corrected to meme.value[index]
};

const applyEdit = (index) => {

  meme.value[index].status = meme.value[index].updatedStatus;
  meme.value[index].editing = -1;
  status_update(index);

};
</script>

<style scoped>
/* Add your custom styles here */
.table {
  width: 100%;
  border-collapse: collapse;
}

.table th,
.table td {
  border: 1px solid #ccc;
  padding: 8px;
}

.status-cell {
  position: relative;
}

.edit-button {
  position: absolute;
  top: 50%;
  right: -3%;
  transform: translateY(-50%);
  padding: 6px 10px;
  cursor: pointer;
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 4px;
}

.edit-button:hover {
  background-color: #0056b3;
}

.action-buttons {
  position: absolute;
  top: 50%;
  right: -3%;
  transform: translateY(-50%);
}

.apply-button,
.cancel-button {
  padding: 6px 10px;
  cursor: pointer;
  color: #fff;
  border: none;
  border-radius: 4px;
  margin-left: 4px;
}

.apply-button:hover {
  background-color: darkgreen;
}

.cancel-button:hover {
  background-color: darkred;
}

.custom-dropdown {
  position: relative;
  display: inline-block;
}

.dropdown-menu {
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
  background-color: #fff;
  color: #333;
  width: 70%;
  /* Adjust the initial width */
  max-width: 150px;
  /* Set a maximum width for responsiveness */
}

.dropdown-arrow {
  position: absolute;
  top: 50%;
  right: 32%;
  /* Adjust the right distance */
  transform: translateY(-50%);
  width: 0;
  height: 0;
  border-style: solid;
  border-width: 6px 6px 0 6px;
  border-color: #666 transparent transparent transparent;
}

.more-link {
  cursor: pointer;
  color: blue;
  text-decoration: underline;
}

.more-link:hover {
  color: darkblue;
}

/* Modal Styles Pop up */
.modal {
  display: block;
  position: fixed;
  z-index: 1000;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  /* Semi-transparent background */
  overflow: auto;
  /* Enable scrolling if content exceeds modal height */
}

.modal-content {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: #fff;
  padding: 20px;
  border-radius: 8px;
  max-width: 80%;
  /* Adjusted maximum width for modal content */
  width: calc(100% - 40px);
  /* Calculate width to leave space for padding */
  max-height: 80%;
  /* Set maximum height for modal content */
  overflow-y: auto;
  /* Enable vertical scrolling within modal content */
}

.close {
  position: absolute;
  top: 10px;
  right: 20px;
  font-size: 20px;
  cursor: pointer;
}

.full-text {
  white-space: pre-wrap;
  /* Preserve line breaks and wrap long lines */
  overflow-wrap: break-word;
  /* Allow long words to wrap within the modal */
}
</style>
