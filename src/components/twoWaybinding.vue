<template>
    <div class="calculator-container">
      <div class="calculator-card">
        <h1>Date Calculator</h1>
        <p>This calculator will add a specified number of days or months to the current date <b>{{ formattedCurrentDate }}</b> and show the end date.</p>
        <div class="input-group">
          <label for="days">Enter number of days</label>
          <input type="number" v-model="days" id="days" />
        </div>
        <button @click="calculateEndDateByDays" class="calculate-btn">Calculate End Date (Days)</button>
        <p v-if="endDateByDays">End Date (Days): {{ endDateByDays }}</p>
  
        <div class="input-group">
          <label for="months">Enter number of months</label>
          <input type="number" v-model="months" id="months" />
        </div>
        <button @click="calculateEndDateByMonths" class="calculate-btn">Calculate End Date (Months)</button>
        <p v-if="endDateByMonths">End Date (Months): {{ endDateByMonths }}</p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        days: 0,
        months: 0,
        endDateByDays: null,
        endDateByMonths: null,
      };
    },
  computed: {
    formattedCurrentDate() {
      const currentDate = new Date();
      return this.formatDate(currentDate);
    }
    },
    methods: {
      formatDate(date) {
        const day = String(date.getDate()).padStart(2, '0');
        const monthNames = [
          "January", "February", "March", "April", "May", "June",
          "July", "August", "September", "October", "November", "December"
        ];
        const month = String(date.getMonth() + 1).padStart(2, '0'); // Numeric month
        const monthName = monthNames[date.getMonth()]; // Get full month name
        const year = date.getFullYear();
        return `${day}-${month}(${monthName})-${year}`;
      },
      calculateEndDateByDays() {
        const currentDate = new Date();
        const calculatedDate = new Date(currentDate);
        calculatedDate.setDate(currentDate.getDate() + parseInt(this.days));
        this.endDateByDays = this.formatDate(calculatedDate);
      },
      calculateEndDateByMonths() {
        const currentDate = new Date();
        const calculatedDate = new Date(currentDate);
        calculatedDate.setMonth(currentDate.getMonth() + parseInt(this.months));
        this.endDateByMonths = this.formatDate(calculatedDate);
      },
    },
  };
  </script>
  
  <style scoped>
  .calculator-container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: #f7f7f9;
  }
  
  .calculator-card {
    background-color: white;
    padding: 30px;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    text-align: center;
    width: 400px;
  }
  
  h1 {
    margin-bottom: 20px;
    font-size: 24px;
    color: #333;
  }
  
  .input-group {
    display: flex;
    align-items: center;
    margin-bottom: 10px;
  }
  
  .input-group label {
    margin-right: -5px;
    font-weight: bold;
    color: #555;
    flex: 0 0 50%;
  }
  
  .input-group input {
    width: 100%;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 5px;
    flex: 1;
  }
  
  .calculate-btn {
    background-color: #007bff;
    color: white;
    border: none;
    padding: 10px 20px;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s;
    margin: 10px 0;
  }
  
  .calculate-btn:hover {
    background-color: #0056b3;
  }
  
  p {
    margin-top: 10px;
    font-size: 16px;
    color: #333;

  }
  </style>
  