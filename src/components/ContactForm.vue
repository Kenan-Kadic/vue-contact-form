<template>
  <form @submit.prevent="submitForm">
  <div class="form title">
    <h3> Contact Us</h3>
    <div class="form-control" :class="{invalid: firstNameValidity === 'invalid'}">
      <label for="first-name">First Name:</label>
      <input id="first-name" name="first-name" type="text" v-model.trim="firstName" @blur="validateFirstName" />
      <p v-if="firstNameValidity === 'invalid'">Please enter a first name!</p>
    </div>
    <div class="form-control" :class="{invalid: lastNameValidity === 'invalid'}">
      <label for="last-name">Last Name:</label>
      <input id="last-name" name="last-name" type="text" v-model.trim="lastName" @blur="validateLastName" />
      <p v-if="lastNameValidity === 'invalid'">Please enter a last name!</p>
    </div>
    <div class="form-control" :class="{invalid: phoneValidity === 'invalid'}">
      <label for="phone">Phone:</label>
      <input id="phone" name="phone" type="tel" v-model.trim="phone" @blur="validatePhone" />
      <p v-if="phoneValidity === 'invalid'">Please enter a valid phone number!</p>
    </div>
    <div class="form-control" :class="{invalid: emailValidity === 'invalid'}">
      <label for="email">Email:</label>
      <input id="email" name="email" type="email" v-model.trim="email" @blur="validateEmail" />
      <p v-if="emailValidity === 'invalid'">Please enter a valid email!</p>
    </div>
    <div class="form-control">
      <label for="product">Product of Interest</label>
      <select id="product" name="product">
        <option selected disabled hidden value></option>
        <option value="bathroom-remodeler">Bathroom Remodeler</option>
        <option value="deck-builder">Deck Builder</option>
        <option value="fence-contractor">Fence Contractor</option>
        <option value="siding-contractor">Siding Contractor</option>
        <option value="windows-installation">Windows Installation Service</option>
        <option value="kitchen-remodeler">Kitchen Remodeler</option>
        <option value="sunroom">Sunroom</option>
        <option value="patio-cover">Patio Cover</option>
      </select>
    </div>
    <div class="form-control" :class="{invalid: aboutValidity === 'invalid'}">
      <label for="about">How did you hear about us? </label>
      <select id="about" name="about" v-model.trim="about" @blur="validateAbout">
        <option selected disabled hidden value></option>
        <option value="online">Online</option>
        <option value="flyer">Flyer/Canvasser</option>
        <option value="phone">Phone</option>
        <option value="radio">Radio</option>
        <option value="referral">Referral</option>
      </select>
      <p v-if="hearAboutUsValidity === 'invalid'">Please make a valid selection!</p>
    </div>
    <div class="form-control" :class="{invalid: messageValidity === 'invalid'}">
      <label for="message">Message: </label>
      <textarea id="message" name="message" type="textarea" rows="4" cols="70" v-model.trim="message" @blur="validateMessage"></textarea>
      <p v-if="messageValidity === 'invalid'">Please enter a valid message!</p>
    </div>
    <div class="form-control">
      <label for="location"> Choose a location: </label>
      <select id="location" name="location">
        <option selected disabled hidden value></option>
        <option value="o-fallon">O'Fallon</option>
        <option value="lees-summit">Lee's Summit (Kansas City)</option>
        <option value="nashville">Nashville</option>
        <option value="wood-dale">Wood Dale (Chicago)</option>
      </select>
    </div>
  </div>
    <button>Submit</button>
    <div>
    <p>DON"T HESITATE. WE'RE HERE TO HELP!</p>
    </div>
  </form>
</template>

<script>
export default {

  data() {
    return {
      firstName: '',
      lastName: '',
      phone: null,
      email: '',
      product: '',
      message: '',
      about: '',
      firstNameValidity: 'pending',
      lastNameValidity: 'pending',
      phoneValidity: 'pending',
      emailValidity: 'pending',
      productValidity: 'pending',
      messageValidity: 'pending',
      aboutValidity: 'pending',
    }
  },

  watch: {
   validateAbout: function(val) {
     if(val == 0) {
       alert('please select a service');
       this.aboutValidity = 'invalid';
       return false;
     } else {
       this.aboutValidity = 'valid';
     }
   }
},

  methods: {
    submitForm(){
      console.log('firstName: ' + this.firstName);
      this.firstName = '';
      console.log('lastName: ' + this.lastName);
      this.lastName = '';
      console.log('phone: ' + this.phone);
      this.phone = null;
      console.log('email ' + this.email);
      this.email = '';
      console.log('product' + this.product);
      this.product = '';
      console.log('message' + this.message);
      this.message = '';

    },

    validateFirstName() {
      if (this.firstName === '') {
        this.firstNameValidity = 'invalid';
      } else {
        this.firstNameValidity = 'valid';
      }
    },
    validateLastName() {
    if (this.lastName === '') {
        this.lastNameValidity = 'invalid';
      } else {
        this.lastNameValidity = 'valid';
      }
    },
    validatePhone() {
    if (this.phone === null) {
        this.phoneValidity = 'invalid';
    } else {
        this.phoneValidity = 'valid';
      }
    },
    validateEmail() {
    if (this.email === '') {
        this.emailValidity = 'invalid';
    } else {
        this.emailValidity = 'valid';
      }
    },
    validateMessage() {
    if (this.message === '') {
        this.messageValidity = 'invalid';
    } else {
        this.messageValidity = 'valid';
      }
    },
  },
};
</script>

<style scoped>
form {
  margin: 2rem auto;
  max-width: 40rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 2rem;
  background-color: #ffffff;
}

.form-control {
  margin: 0.5rem 0;
}

.form-control.invalid input {
  border-color: red;
}

.form-control.invalid label {
  color: red;
}

label {
  font-weight: bold;
}

h2 {
  font-size: 1rem;
  margin: 0.5rem 0;
}

input,
select {
  display: block;
  width: 100%;
  font: inherit;
  margin-top: 0.5rem;
}

select {
  width: auto;
}

button {
  font: inherit;
  border: 1px solid #0076bb;
  background-color: #0076bb;
  color: white;
  cursor: pointer;
  padding: 0.75rem 2rem;
  border-radius: 30px;
}

button:hover,
button:active {
  border-color: #002350;
  background-color: #002350;
}
</style>