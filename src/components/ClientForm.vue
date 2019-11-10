<template>
  <div id="client-form">
    <form @submit.prevent="handleSubmit">
      <label>From Date</label>
      <datepicker placeholder="Select Date" :class="{ 'has-error': submitting && invalidFromDate }" v-model="fromDate" @focus="clearStatus" @keypress="clearStatus"></datepicker>
      <label>To Date</label>
      <datepicker placeholder="Select Date" :class="{ 'has-error': submitting && invalidToDate }" v-model="toDate" @focus="clearStatus" @keypress="clearStatus"></datepicker>
      <p v-if="error && submitting" class="error-message">
        ❗Please fill out all required fields
      </p>
      <button>Search</button>
    </form>
  </div>
</template>


<script>
  export default {
    name: 'client-form',
    data() {
      return {
        dates: {
          fromDate: '',
          toDate: '',
        },
        submitting: false,
        error: false,
        success: false,
      }
    },
    methods: {
      handleSubmit() {
        this.submitting = true
        this.clearStatus()

        if (this.invalidFromDate || this.invalidToDate) {
          this.error = true
          return
        }

        this.$emit('add:client', this.client)
        this.error = false
        this.success = true
        this.submitting = false
      },

      clearStatus() {
        this.success = false
        this.error = false
      },
    },
    computed: {
      invalidFromDate() {
        return this.fromDate === ''
      },

      invalidToDate() {
        return this.toDate === ''
      },
    },
  }
</script>

<style scoped>
  form {
    margin-bottom: 2rem;
  }

  [class*='-message'] {
    font-weight: 500;
  }

  .error-message {
    color: #d33c40;
  }

  .success-message {
    color: #32a95d;
  }
</style>