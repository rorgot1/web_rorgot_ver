<template>
    <div>
        <button @click="test_api">กดฉัน</button>
    </div>
</template>

<script setup>
const State = ref();
const test_api = async () => {
    try{
        const response = await $fetch('http://localhost:5600/api/IT_Repair_status_choice', {
            method : "POST",
            credentials : 'include'
        })
        State.value =response.results
        console.log(State.value)

    }catch (error){
    console.error('Failed to fetch test_api data:', error);
    }
}
</script>

<style scoped>
button {
    padding: 10px 20px;
    font-size: 16px;
    background-color: #007bff;
    color: #fff;
    border: none;
    cursor: pointer;
}
</style>