<template>
    <div class="homepage">
      <!-- IE Bank Logo -->
  
      <!-- Welcome Text -->
      <h1>Jannik Wendt IE Bank</h1>
      <p>IE BANK CORP</p>
      
      <!-- View Accounts Button -->
      <button @click="viewAccounts">View Accounts</button>
    </div>
  </template>
  
  <script>
  export default {
    methods: {
      viewAccounts() {
        // Logic to navigate to the accounts page or handle the button click
        alert('Navigating to the accounts page...');
        // You can implement navigation here, for example:
        this.$router.push('/accounts');
      }
    }
  };
  </script>
  
  <style scoped>
  .homepage {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    text-align: center;
    background-color: #f2f2f2;
  }
  
  .logo {
    width: 100px; /* Adjust the size of the logo */
    margin-bottom: 20px;
  }
  
  h1 {
    color: #001f3f; /* Dark blue color */
    font-size: 2.5rem;
    margin-bottom: 10px;
  }
  
  p {
    font-size: 1.2rem;
    color: #555;
    margin-bottom: 30px;
  }
  
  button {
    padding: 10px 20px;
    background-color: #001f3f; /* Dark blue background for button */
    color: white;
    border: none;
    border-radius: 4px;
    font-size: 1.2rem;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #003366; /* Slightly lighter blue on hover */
  }
  </style>