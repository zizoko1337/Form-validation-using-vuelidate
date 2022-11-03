<!-- please don't look at the inputs. i used random form generator so i could finish this test faster. Thats why input classes names and id's are weird. I just dont need tho change them cuz this is a small test project -->
<template>
  <div class="rendered-form">
    <div class="">
      <h1>Form Validation Test</h1>
    </div>
    <div class="formbuilder-text form-group field-text-1667487215001">
      <label for="text-1667487215001" class="formbuilder-text-label"
        >Text Field<span class="formbuilder-required">*</span></label
      >
      <input
        v-model="text"
        type="text"
        class="form-control"
        name="text-1667487215001"
        access="false"
        id="text-1667487215001"
        required="required"
        aria-required="true"
      />
      <span v-if="v$.text.$error" class="error">this field is required</span>
    </div>
    <div class="formbuilder-text form-group field-text-1667487281471">
      <label for="text-1667487281471" class="formbuilder-text-label"
        >Email<span class="formbuilder-required">*</span></label
      >
      <input
        v-model="email"
        type="email"
        class="form-control"
        name="text-1667487281471"
        access="false"
        id="text-1667487281471"
        required="required"
        aria-required="true"
      />
    </div>
    <span v-if="v$.email.$error" class="error">incorrect email</span>
    <div class="formbuilder-text form-group field-text-1667487227514">
      <label for="text-1667487227514" class="formbuilder-text-label"
        >Password<span class="formbuilder-required">*</span></label
      >
      <input
        v-model="password"
        type="password"
        class="form-control"
        name="text-1667487227514"
        access="false"
        id="text-1667487227514"
        required="required"
        aria-required="true"
      />
      <span v-if="v$.password.$error" class="error">password need to be at least 6 characters long</span>
    </div>
    <div class="formbuilder-select form-group field-select-1667487381449">
      <label for="select-1667487381449" class="formbuilder-select-label"
        >Select your skills</label
      >
      <select
        v-model="skills"
        class="form-control"
        name="select-1667487381449"
        id="select-1667487381449"
      >
        <option value="option-1" id="select-1667487381449-0">Frontend</option>
        <option value="option-2" id="select-1667487381449-1">Backend</option>
        <option value="option-3" id="select-1667487381449-2">Fullstack</option>
      </select>
      <span v-if="v$.skills.$error" class="error">please select one option</span>
    </div>
    <div
      class="formbuilder-checkbox-group form-group field-checkbox-group-1667487598161"
    >
      <label
        for="checkbox-group-1667487598161"
        class="formbuilder-checkbox-group-label"
        >Frameworks</label
      >
      <div class="checkbox-group">
        <div class="formbuilder-checkbox-inline">
          <input
            name="checkbox-group-1667487598161[]"
            access="false"
            id="checkbox-group-1667487598161-0"
            value="option-1"
            type="checkbox"
            checked="checked"
          />
          <label for="checkbox-group-1667487598161-0">Vue</label>
        </div>
        <div class="formbuilder-checkbox-inline">
          <input
            name="checkbox-group-1667487598161[]"
            access="false"
            id="checkbox-group-1667487598161-1"
            type="checkbox"
          />
          <label for="checkbox-group-1667487598161-1">React</label>
        </div>
        <div class="formbuilder-checkbox-inline">
          <input
            name="checkbox-group-1667487598161[]"
            access="false"
            id="checkbox-group-1667487598161-2"
            type="checkbox"
          />
          <label for="checkbox-group-1667487598161-2">Angular</label>
        </div>
      </div>
    </div>
    <div class="formbuilder-file form-group field-file-1667487495601">
      <label for="file-1667487495601" class="formbuilder-file-label"
        >CV</label
      >
      <input
        type="file"
        class="form-control"
        name="file-1667487495601"
        access="false"
        multiple="false"
        id="file-1667487495601"
        aria-required="true"
      />
    </div>
    <div class="formbuilder-button form-group field-button-1667490653013">
        <button @click="submitForm" type="submit" class="btn-success btn" name="button-1667490653013" access="false" style="success" id="button-1667490653013">Submit</button>
    </div>
    <span class="formbuilder-required">*</span> = required fields
  </div>
</template>

<script>
import useValidate from '@vuelidate/core'
import { required, email, minLength } from '@vuelidate/validators'

export default {
  name: 'VueForm',
  props: {
    msg: String,
  },
  data() {
    return {
      v$: useValidate(),
      text: '',
      email: '',
      password: '',
      skills: '',
    };
  },
  validations() {
    return {
      text: { required },
      email: { required, email },
      password: { required, minLength: minLength(6) },
      skills: { required },
    }
  },
  methods: {
    submitForm() {
      this.v$.$validate()
      if(!this.v$.$error){
        alert("success - all required fields were properly submitted to our secret database 👽")
      }else{
        console.log("💩")
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
input { 
    text-align: center; 
}
label {
  font-weight: 600;
  margin-top: 1vh;
}
button {
  margin-top: 2vh;
}
option {
  text-align: center;
}
.rendered-form {
  max-width: 80vh;
  margin: auto;
  text-align: center;
}
.formbuilder-required {
  color: #42b983;
}
.formbuilder-checkbox-inline {
  display: inline;
  margin: 0.5vh;
}
.form-control:focus {
  border-color: #42b983;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 8px rgba(0, 255, 136, 0.6);
}
.error {
  font-weight: 600;
  color: red;
}

</style>
