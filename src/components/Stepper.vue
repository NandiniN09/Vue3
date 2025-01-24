<template>
  <div class="stepper-container">
    <!-- Stepper Header -->
    <div class="stepper-header">
      <div
        v-for="(step, index) in steps"
        :key="index"
        :class="[
          'step',
          { active: currentStep === index, completed: index < currentStep },
        ]"
      >
        <div class="step-number">{{ index + 1 }}</div>
        <div class="step-title">{{ step.title }}</div>
      </div>
    </div>

    <!-- Stepper Content -->
    <div class="stepper-content">
      <template v-if="currentStep === 0">
        <h3>{{ steps[0].title }}</h3>
        <div>
          <label>
            <input type="radio" value="Credit Card" v-model="paymentMethod" />
            Credit Card
          </label>
          <label>
            <input type="radio" value="PayPal" v-model="paymentMethod" />
            PayPal
          </label>
          <label>
            <input type="radio" value="Bank Transfer" v-model="paymentMethod" />
            Bank Transfer
          </label>
        </div>
      </template>

      <template v-if="currentStep === 1">
        <h3>{{ steps[1].title }}</h3>
        <select v-model="bank" required>
          <option disabled value="">Select your bank</option>
          <option value="Bank of America">Bank of America</option>
          <option value="Chase Bank">Chase Bank</option>
          <option value="Wells Fargo">Wells Fargo</option>
        </select>
      </template>

      <template v-if="currentStep === 2">
        <h3>{{ steps[2].title }}</h3>
        <p><strong>Payment Method:</strong> {{ paymentMethod }}</p>
        <p><strong>Bank:</strong> {{ bank }}</p>
        <p>Click "Confirm" to finalize your choices.</p>
      </template>
    </div>

    <!-- Stepper Actions -->
    <div class="stepper-actions">
      <button @click="prevStep" :disabled="currentStep === 0">Previous</button>
      <button
        @click="nextStep"
        :disabled="!canProceed"
        v-if="currentStep < steps.length - 1"
      >
        Next
      </button>
      <button @click="confirm" v-if="currentStep === steps.length - 1">
        Confirm
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Stepper',
  data() {
    return {
      currentStep: 0,
      paymentMethod: null,
      bank: '',
      steps: [
        { title: 'Select Payment Method' },
        { title: 'Enter Bank Details' },
        { title: 'Confirm Details' },
      ],
    };
  },
  computed: {
    canProceed() {
      // Step 1: Ensure a payment method is selected
      if (this.currentStep === 0) {
        return this.paymentMethod !== null;
      }
      // Step 2: Ensure a bank is selected
      if (this.currentStep === 1) {
        return this.bank !== '';
      }
      return true;
    },
  },
  methods: {
    nextStep() {
      if (this.currentStep < this.steps.length - 1) {
        this.currentStep++;
      }
    },
    prevStep() {
      if (this.currentStep > 0) {
        this.currentStep--;
      }
    },
    confirm() {
      alert(
        `Payment Method: ${this.paymentMethod}\nBank: ${this.bank}\nConfirmation Successful!`
      );
    },
  },
};
</script>

<style scoped>
.stepper-container {
  max-width: 600px;
  margin: 20px auto;
  text-align: center;
  font-family: Arial, sans-serif;
}

.stepper-header {
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
}

.step {
  display: flex;
  flex-direction: column;
  align-items: center;
  flex: 1;
}

.step-number {
  width: 30px;
  height: 30px;
  line-height: 30px;
  border: 2px solid #ccc;
  border-radius: 50%;
  background-color: #fff;
  margin-bottom: 5px;
  font-weight: bold;
}

.step-title {
  font-size: 14px;
}

.step.active .step-number {
  border-color: #007bff;
  background-color: #007bff;
  color: #fff;
}

.step.completed .step-number {
  border-color: #28a745;
  background-color: #28a745;
  color: #fff;
}

.stepper-content {
  margin-bottom: 20px;
  font-size: 16px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.stepper-actions button {
  padding: 10px 15px;
  margin: 0 5px;
  font-size: 14px;
  border: none;
  background-color: #007bff;
  color: #fff;
  cursor: pointer;
  border-radius: 4px;
}

.stepper-actions button:disabled {
  background-color: #ccc;
  cursor: not-allowed;
}
</style>
