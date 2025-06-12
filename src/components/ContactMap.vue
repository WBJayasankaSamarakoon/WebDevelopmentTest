<template>
  <section class="contact-container">
    <div class="contact-content">
      <!-- First content section -->
      <div class="content-section">
        <div class="text-content">
          <h1>How to reach us</h1>
          <p>Lorem ipsum dolor sit amet, consectetur.</p>
        </div>
      </div>

      <!-- Second content section with form and map -->
      <div class="form-map-section">
  <div class="contact-form">
    <form @submit.prevent="handleSubmit" novalidate>
      <div class="form-row">
        <div class="form-group name-group" :class="{ 'has-error': errors.firstName }">
          <label for="firstName">First Name *</label>
          <input
            type="text"
            id="firstName"
            v-model="form.firstName"
            @input="clearError('firstName')"
          />
          <span v-if="errors.firstName" class="error-message">{{ errors.firstName }}</span>
        </div>

        <div class="name-spacer"></div>

        <div class="form-group name-group" :class="{ 'has-error': errors.lastName }">
          <label for="lastName">Last Name</label>
          <input
            type="text"
            id="lastName"
            v-model="form.lastName"
            @input="clearError('lastName')"
          />
          <span v-if="errors.lastName" class="error-message">{{ errors.lastName }}</span>
        </div>
      </div>

      <div class="form-group" :class="{ 'has-error': errors.email }">
        <label for="email">Email *</label>
        <input
          type="email"
          id="email"
          v-model="form.email"
          @input="clearError('email')"
        />
        <span v-if="errors.email" class="error-message">{{ errors.email }}</span>
      </div>

      <div class="form-group" :class="{ 'has-error': errors.telephone }">
        <label for="telephone">Telephone</label>
        <input
          type="tel"
          id="telephone"
          v-model="form.telephone"
          @input="clearError('telephone')"
        />
        <span v-if="errors.telephone" class="error-message">{{ errors.telephone }}</span>
      </div>

      <div class="form-group" :class="{ 'has-error': errors.message }">
        <label for="message">Message</label>
        <textarea
          id="message"
          rows="4"
          v-model="form.message"
          @input="clearError('message')"
        ></textarea>
        <span v-if="errors.message" class="error-message">{{ errors.message }}</span>
      </div>

      <div class="required-note">* required fields</div>

      <div class="checkbox-group">
        <input type="checkbox" id="terms" v-model="form.agreeTerms" />
        <label for="terms">I agree to the <span class="underline-text">Terms & Conditions</span></label>
      </div>

      <div class="divider"></div>

      <button type="submit" class="submit-btn">SUBMIT</button>

    </form>
  </div>


        <div class="map-container">
          <iframe
            src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3036.7358940487925!2d-3.660970523309557!3d40.436846671436165!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0xd422f35d4f0c269%3A0x754405946e8ca584!2sAmadeus%20IT%20Group!5e0!3m2!1sen!2slk!4v1749743690720!5m2!1sen!2slk"
            width="100%"
            height="100%"
            style="border:0;"
            allowfullscreen=""
            loading="lazy"
            referrerpolicy="no-referrer-when-downgrade"
            title="Amadeus IT Headquarters Map"
          ></iframe>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { reactive } from "vue";

const form = reactive({
  firstName: "",
  lastName: "",
  email: "",
  telephone: "",
  message: "",
  agreeTerms: false,
});

const errors = reactive({
  firstName: "",
  lastName: "",
  email: "",
  telephone: "",
  message: "",
});

function validateEmail(email) {
  const re = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  return re.test(email);
}

function clearError(field) {
  errors[field] = "";
}

function handleSubmit() {
  Object.keys(errors).forEach((key) => (errors[key] = ""));

  let valid = true;

  if (!form.firstName.trim()) {
    errors.firstName = "First name is required";
    valid = false;
  }
  if (!form.email.trim()) {
    errors.email = "Email is required";
    valid = false;
  } else if (!validateEmail(form.email)) {
    errors.email = "Please enter a valid email";
    valid = false;
  }
  if (!form.agreeTerms) {
    alert("You must agree to the Terms & Conditions");
    valid = false;
  }

  if (!valid) return;

  alert(
    `Form submitted with:\nFirst Name: ${form.firstName}\nLast Name: ${form.lastName}\nEmail: ${form.email}\nTelephone: ${form.telephone}\nMessage: ${form.message}`
  );

  form.firstName = "";
  form.lastName = "";
  form.email = "";
  form.telephone = "";
  form.message = "";
  form.agreeTerms = false;
}
</script>

<style scoped>
.contact-container {
  background-color: #000;
  color: #fff;
  padding: 2rem 0;
  font-family: 'Open Sans', 'Gotham', Arial, sans-serif;
}

.contact-content {
  display: flex;
  flex-direction: column;
  max-width: 1980px;
  margin: 0 auto;
  gap: 3rem;
  padding: 0 2rem;
}

.content-section {
  width: 100%;
}

.text-content {
  max-width: 1980px;
  margin: 0 auto;
  font-size: large;
}

.form-map-section {
  display: flex;
  gap: 3rem;
  width: 100%;
}

.contact-form {
  flex: 1;
  min-width: 0;
}

.map-container {
  flex: 1;
  min-height: 700px;
  border-radius: 8px;
  overflow: hidden;
}

h1 {
  font-size: 1.8rem;
  margin-bottom: 0.8rem;
}

p {
  margin-bottom: 1.5rem;
  color: #aaa;
}

.divider {
  height: 1px;
  background-color: #333;
  margin: 1.5rem 0;
}

.form-row {
  display: flex;
  gap: 1.5rem;
  margin-bottom: 1.5rem;
}

.form-group {
  flex: 1;
}

.name-spacer {
  width: 15px;
}

.form-row {
  display: flex;
  align-items: flex-start;
  margin-bottom: 1.5rem;
}

.form-group:not(:last-child) {
  margin-bottom: 1.5rem;
}

label {
  display: block;
  margin-bottom: 0.5rem;
  font-size: 0.9rem;
  color: #ccc;
}

.underline-text {
  text-decoration: underline;
}


input[type="text"],
input[type="email"],
input[type="tel"],
textarea {
  width: 100%;
  padding: 0.8rem;
  border: 1px solid #333;
  border-radius: 4px;
  font-size: 1rem;
  background-color: #111;
  color: #fff;
}

textarea {
  min-height: 120px;
  resize: vertical;
}

.has-error input,
.has-error textarea {
  border-color: #e74c3c;
}

.error-message {
  color: #e74c3c;
  font-size: 0.85rem;
  margin-top: 0.25rem;
  display: block;
}

.required-note {
  font-size: 0.8rem;
  color: #888;
  margin-bottom: 1.5rem;
}

.checkbox-group {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
}

.checkbox-group input {
  width: auto;
}

.checkbox-group label {
  margin-bottom: 0;
  color: #ccc;
}

.name-group {
  flex: 1;
}

.submit-btn {
  background-color: #b98f02 ;
  color: white;
  border: none;
  padding: 1.2rem 2rem;
  font-size: 1rem;
  font-weight: bold;
  cursor: pointer;
  width: 50%;
  text-transform: uppercase;
  border-radius: 4px;
  transition: background-color 0.3s;
  margin: 1rem 0 1rem auto;
  display: block; 
}

.submit-btn:hover {
  background-color: #9c7802;
}

@media (max-width: 768px) {
  .contact-content {
    padding: 0 1rem;
  }
  
  .form-map-section {
    flex-direction: column;
    gap: 2rem;
  }
  
  .map-container {
    min-height: 400px;
  }

  .form-row {
    flex-direction: column;
    gap: 0;
    margin-bottom: 0;
  }
}
</style>