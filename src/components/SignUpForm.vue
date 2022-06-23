<template>
  <form @submit.prevent="handleSubmit">
    <label>Email: </label>
    <input type="email" v-model="email" required />

    <label>Password: </label>
    <input type="password" v-model="password" required />
    <p v-if="passwordError" class="error">{{passwordError}}</p>

    <label>Role: </label>
    <select v-model="role">
      <option value="developer">Web Developer</option>
      <option value="blockchain">Blockchain Developer</option>
      <option value="designer">Web Designer</option>
      <option value="engineer">ML Enginner</option>
    </select>

    
    <label>Skills: </label>
    <input type="text" v-model="tempSkill" @keyup="addSkill" />
    <div v-for="skill in skills" :key="skill" class="pill">
      <span @click="removeSkill(skill)">{{ skill }}</span>
    </div>

    <div>
      <input type="checkbox" v-model="check" required />
      <label>Accepts Terms and Conditions</label>
    </div>

    <div class="submit">
      <button>Create an Account</button>
    </div>

  </form>
</template>

<script>

export default {
  name: "SignUpForm",
  data() {
    return {
      email: "",
      password: "",
      role: "",
      check: false,
      tempSkill: '',
      skills: [],
      passwordError: ''
    }
  },

  methods: {
    addSkill(e) {
      // console.log(e)
      if(e.key === ',' && this.tempSkill) {
        if(!this.skills.includes(this.tempSkill)) {
           this.skills.push(this.tempSkill); 
        }
        this.tempSkill = '';
      }
    },

    removeSkill(skill) {
      this.skills = this.skills.filter(item => item !== skill)
    },

    handleSubmit() {
      // validate password
      this.passwordError = this.password.length > 5 ? 
      "" : "Password must be at least 6 character long"

      if(!this.passwordError) {
        console.log("Email: ", this.email);
        console.log("Password: ", this.password);
        console.log("Role: ", this.role);
        console.log("Skills: ", this.skills);
        console.log("Terms: ", this.check);
      }
    }
  }
}
</script>

<style>
 form {
  max-width: 420px;
  margin: 30px auto;
  background: white;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
 }

 label {
  color: rgb(121, 120, 120);
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 0.6em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
 }

 input, select {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  outline: none;
  border-bottom: 1px solid #ddd;
  color: #555;
 }

 input[type="checkbox"] {
  display: inline-block;
  width: 16px;
  margin:  0 10px 0 0;
  position: relative;
  top: 2px;
 }
 .pill {
  display: inline-block;
  margin: 20px 10px 0 0;
  padding: 6px 12px;
  background-color: rgb(82, 39, 255);
  color: white;
  font-size: 12px;
  letter-spacing: 1px;
  font-weight: bold;
  cursor: pointer;
 }
 button{
  background-color: rgb(80, 61, 253);
  border: 0;
  padding: 10px 20px;
  margin-top: 30px;
  margin-bottom: 10px;
  color: white;
  cursor: pointer;
  width: 100%;
 }
 .submit {
  text-align: center;
 }
 .error {
  background: red;
  color: white;
  font-size:12px;
  font-weight: bold;
  margin-bottom: 10px;
  padding: 5px 5px;
 }
 
</style>