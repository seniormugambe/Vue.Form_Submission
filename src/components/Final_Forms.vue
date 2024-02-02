<template>
    
      <form @submit.prevent="submitForm" class="form-container">
        <!-- form fields here -->
        <label for="full_name">Full Name:</label>
        <input v-model="formData.full_name" type="text" id="full_name" />
      

      <div>
        <label for="email">Email:</label>
        <input v-model="formData.email" type="email" id="email" />
      </div>

      <div>
        <label for="password">Password:</label>
        <input v-model="formData.password" type="text" id="password" />
      </div>
      <label for="username">Username:</label>
        <input v-model="formData.username" type="text" id="username" />
      

      <div>
        <label for="partner_id">Partner ID:</label>
        <input v-model="formData.partner_id" type="text" id="partner_id" />
      </div>

      <div>
        <label for="phone_number">Phone Number:</label>
        <input v-model="formData.phone_number" type="text" id="phone_number" />
      </div>

      <label for="role">Role:</label>
      <select  v-model="formData.role" id="role" name="role">
          <option value="admin">Admin</option>
      <option value="finance">Finance</option>
      <option value="healthcare">Healthcare</option>
        <option value="tech">Tech(I.T)</option>
    </select>
      <div>
        <label for="roles" class="label">Roles:</label>
        
        <select v-model="roles" id="roles" name="roles" multiple class="select-container">
      <option value="view_customers">Can view customers</option>
      <option value="write_customers">Can write customers</option>

      
      
      <option value="view_nurses">Can view nurses</option>
      <option value="write_nurses">Can write nurses</option>

      
      
      <option value="view_jobs">Can view jobs</option>
      <option value="write_jobs">Can write jobs</option>
      
    </select>
      </div>

      <div>
       <!---- /*<label for="sex">Sex:</label>
        <input v-model="formData.sex" type="text" id="sex" />-->



        <label> <input type="radio" v-model="sex" value="male" name="gender" />Male</label>

    <label>
      <input
        type="radio" v-model="sex" value="female" name="gender" />
      Female
    </label>

    <label>
      <input type="radio" v-model="sex" value="other" name="gender"/>Other
    </label>



      </div>

      <div>
        <label for="status">Status:</label>
<select  v-model="status" id="status" name="status">
          <option value="active">Active</option>
      <option value="disabled">Disabled</option>
      <option value="suspended">Suspended</option>
      
  </select>
      </div>
        <button type="submit" class="submit-button">Submit</button>
      </form>
    
  </template>
   
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        formData: {
            full_name:'',
          username: '',
          email: '',
          password: '',
          partner_id :'',
          phone_number:'',
          role:"",
          roles:"",
          sex:"",
          status:""
        },

       

      };
    },
    methods: {
      async submitForm() {
        try {
          const headers = {
            'Content-Type': 'application/json',
            'User-Agent': 'insomnia/8.4.2',
            header: process.env.VUE_APP_HEADER
          };
  
          const response = await axios.post('https://staging-api.teheca.com/api/v1/auth/register', this.formData, {
            headers: headers,
          });
  
          console.log('API response:', response.data);
        } catch (error) {
          console.error('Error submitting form:', error.message);
        }
      },
    },
  };
  </script>

	
<style scoped>


.form-container {
  max-width: 400px;
  margin: auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  background-color: #21aa28;
  font-size: large;
  font-weight: bold;
}

.label {
  display: block;
  margin-bottom: 8px;
  font-weight: bold;
}

.select-box {
  width: 100%;
  padding: 8px;
  margin-bottom: 16px;
  box-sizing: border-box;
}

.submit-button {
  background-color: #4caf50;
  color: white;
  padding: 10px 15px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 16px;
}

.submit-button:hover {
  background-color: #1e06a7;
}


</style>