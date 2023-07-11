<script setup>
import { ref } from 'vue';

const partner = ref('');
const accountNumber = ref('');
const firstName = ref('');
const lastName = ref('');
const address = ref('');
const city = ref('');
const state = ref('');
const zip = ref('');
const contactPhone = ref('');
const contactEmail = ref('');
const customerType = ref('');
const phoneNumber = ref('');
const sipPassword = ref('');
const ported = ref('');
const bypassE911 = ref(false);

const submitForm = () => console.log('Form submitted');
</script>

<template>
  <div class="header-wrapper">
    <h1 class="header">Voice Provisioning</h1>
  </div>

  <div class="form-wrapper">
    <form
      class="form"
      @submit.prevent="submitForm">
      <div class="form-row">
        <select class="select" v-model="partner">
          <option
            value=""
            selected
          >
            Select a Partner
          </option>
          <option value="partner1">Partner 1</option>
          <option value="partner2">Partner 2</option>
          <option value="partner3">Partner 3</option>
        </select>
      </div>

      <div class="form-row">
        <input
          v-model.trim="accountNumber"
          type="text"
          class="input-field"
          placeholder="Account number" />
      </div>

      <div class="form-row row-input">
        <div class="input-container">
          <input
            v-model.trim="firstName"
            type="text"
            class="input-field"
            placeholder="First Name" />
        </div>

        <div class="input-container">
          <input
            v-model.trim="lastName"
            type="text"
            class="input-field"
            placeholder="Last Name" />
        </div>
      </div>

      <div class="form-row row-input">
        <div class="input-container">
          <input
            v-model.trim="address"
            type="text"
            class="input-field"
            placeholder="Address" />
        </div>

        <div class="input-container">
          <input
            v-model.trim="city"
            type="text"
            class="input-field"
            placeholder="City" />
        </div>

        <div class="input-container">
          <input
            v-model.trim="state"
            type="text"
            class="input-field"
            placeholder="State" />
        </div>

        <div class="input-container">
          <input
            v-model.trim="zip"
            type="text"
            class="input-field"
            placeholder="Zip" />
        </div>
      </div>

      <div class="form-row row-input">
        <div class="input-container">
          <input
            v-model.trim="contactPhone"
            type="tel"
            class="input-field"
            placeholder="Contact Phone" />
        </div>

        <div class="input-container">
          <input
            v-model.trim="contactEmail"
            type="email"
            class="input-field"
            placeholder="Contact Email" />
        </div>
      </div>

      <div class="form-row row-input">
        <div class="input-container">
          <select
            v-model="customerType"
            class="select"
          >
            <option
              value=""
              selected>
              Customer Type
            </option>
            <option value="type1">Type 1</option>
            <option value="type2">Type 2</option>
            <option value="type3">Type 3</option>
          </select>
        </div>

        <div class="input-container">
          <input
            v-model.trim="phoneNumber"
            type="text"
            class="input-field"
            placeholder="Phone Number to Provision" />
        </div>

        <div class="input-container">
          <input
            v-model.trim="sipPassword"
            type="text"
            class="input-field"
            placeholder="Sip Password" />
        </div>
      </div>

      <div class="form-row row-input">
        <select
          v-model="ported"
          class="select select-posted"
        >
          <option
            value=""
            selected
          >
            Ported
          </option>
          <option value="yes">Yes</option>
          <option value="no">No</option>
        </select>
      </div>

      <div class="form-row row-input">
        <div class="bypass-checkbox">
          <label for="bypass">
            <input
              v-model="bypassE911"
              type="checkbox"
              id="bypass"
              class="checkbox-input"/>
            Bypass E911 Address Automation
          </label>
        </div>

        <div class="wrapper-warning" :class="{ 'hidden': bypassE911 }">
            <div class="warning-sign">
            <img
              src="/image/danger.svg"
              class="warning-icon"
              alt="warning sign" />
          </div>
          <div class="attention">
            (By checking "Bypass E911 Address Automation" you agree to manually
            add this phone number and address to Bandwidth)
          </div>
        </div>
      </div>

      <div class="form-row">
        <button type="submit" class="provision-button">PROVISION</button>
      </div>
    </form>
  </div>
</template>

<style scoped>
.header-wrapper {
  margin: 0 auto;
  margin-top: 100px;
  text-align: center;
  box-shadow: 0 -1px 1px 0 rgba(60, 64, 67, 0.3);
}
.header {
  padding: 10px;
  font-size: 20px;
}
.form-wrapper {
  max-width: 1024px;
  margin: 0 auto;
}
.form {
  display: flex;
  flex-direction: column;
  color: #80868b;
}
.form-row {
  margin-bottom: 30px;
}
.form input:focus,
.form select:focus {
  outline: none;
}

.select {
  background-color: rgba(187, 228, 242, 0.3);
  padding: 10px;
  border-radius: 5px;
  border: none;
  box-shadow: 0 1px 3px 0 rgba(60, 64, 67, 0.3);
  color: #80868b;
  width: 100%;
}
.input-container {
  flex-grow: 1;
}
.row-input {
  display: flex;
  align-items: center;
  gap: 20px;
}
.input-field {
  background-color: rgba(187, 228, 242, 0.3);
  box-shadow: 0 1px 3px 0 rgba(60, 64, 67, 0.3);
  padding: 10px;
  width: 100%;
  border-radius: 5px;
  text-align: left;
}
.select-posted {
  width: 30%;
}
.bypass-checkbox {
  display: flex;
  align-items: center;
  height: 60px;
  width: 40%;
  font-size: 12px;
}
.wrapper-warning {
  display: flex;
  padding: 5px 5px;
  border: 1px solid rgb(150, 104, 3);
  border-radius: 3px;
  justify-content: space-between;
  align-items: center;

  transition: opacity 0.3s ease-in-out;
  overflow: hidden;
}
.hidden {
  opacity: 0;
}
.warning-icon {
  width: 40px;
  height: 40px;
}
.attention {
  color: rgb(214, 150, 11);
  border-radius: 3px;
  padding: 5px 5px;
  font-size: 14px;
}
.checkbox-input {
  font-size: 10px;
}
.provision-button {
  padding: 10px 20px;
  background-color: rgb(43, 18, 97);
  color: white;
  font-size: 10px;
  border: none;
  border-radius: 5px;
  margin-left: auto;
}
</style>
