<template>
  <div id="app">
    <form-wizard>
      <template v-slot="{registration}">
        <tab name="Step 1" info="Your name and Email" :selected="true" :registration="registration">
              <div id="form-step-1" >
                  <div class="field">
                      <label class="label">Name</label>
                      <div class="control">
                          <input class="input" name="fullname" type="text" placeholder="Text input"  v-model="registration.name" data-vv-scope="step1" v-validate="'required'">
                          <p class="help is-danger" v-show="errors.has('step1.fullname')">
                                  {{ errors.first('step1.fullname') }}
                          </p>
                      </div>
                  </div>
      
                  <div class="field">
                          <label class="label">Email</label>
                          <div class="control">
                            <input class="input" name="email"  type="email"  v-model="registration.email" placeholder="Email input" data-vv-scope="step1" v-validate="'required|email'">
                            <p class="help is-danger" v-show="errors.has('step1.email')">
                                  {{ errors.first('step1.email') }}
                              </p>
                          </div>
                  </div>
              </div>
          </tab>
          <tab name="Step 2" info="Basic Info about you" data-vv-scope="step2">
              <div id="form-step-2">
                      <div class="field">
                              <label class="label">About you</label>
                              <div class="control">
                                <textarea class="textarea" name="about"  v-model="registration.about" placeholder="Something about you.." v-validate="'required'" data-vv-scope="step2"></textarea>
                                <p class="help is-danger" v-show="errors.has('step2.about')">
                                      {{ errors.first('step2.about') }}
                                </p>
                              </div>
                        </div>
                        <div class="field">
                              <div class="control">
                                  <strong>Gender</strong><br/>
                                <label class="radio">
                                  <input type="radio" name="gender" v-model="registration.gender" v-validate="'required'" data-vv-scope="step2" value="Male">
                                  Male
                                </label>
                                <label class="radio">
                                  <input type="radio" name="gender" v-model="registration.gender" data-vv-scope="step2" value="Female">
                                  Female
                                </label>
                                <p class="help is-danger" v-show="errors.has('step2.gender')">
                                      {{ errors.first('step2.gender') }}
                                </p>
                              </div>
                        </div>
              </div>
          </tab>
          <tab name="Step 3" info="Finishing Up" >
              <div id="form-step-3">
                      <div class="field">
                              <label class="label">Where did you hear about us?</label>
                              <div class="control">
                                <div class="select" name="reference">
                                  <select v-model="registration.reference" v-validate="'required'" name="reference" data-vv-scope="step3">
                                    <option value="">Select</option>
                                    <option value="newspaper">Newspaper</option>
                                    <option value="social-media">Social Media</option>
                                    <option value="other">Other</option>
                                  </select>
                                </div>
                              </div>
                              <p class="help is-danger" v-show="errors.has('step3.reference')">
                                      {{ errors.first('step3.reference') }}
                              </p>
                      </div>
                      <div class="field">
                              <div class="control">
                                <label class="checkbox">
                                  <input type="checkbox" name="terms" v-model="registration.terms" data-vv-scope="step3" v-validate="'required'">
                                  I agree to the <a href="#">terms and conditions</a>
                                </label>
                              </div>
                              <p class="help is-danger" v-show="errors.has('step3.terms')">
                                      {{ errors.first('step3.terms') }}
                              </p>
                      </div>                
              </div>
          </tab>
          </template>
          </form-wizard>

  </div>
</template>

<script>
import Vue from 'vue';
import VeeValidate from 'vee-validate';
import FormWizard from './components/FormWizard.vue';
import Tab from './components/Tab.vue';
import 'bulma/css/bulma.css'

Vue.use(VeeValidate);

export default {
  name: 'app',
  components: {
    FormWizard, Tab
  },
}
</script>

<style lang="scss">

@import "./../node_modules/bulma/bulma.sass";
@import "./../node_modules/bulma-steps-component/bulma-steps.sass";

body{
   padding: 40px;
}

[v-cloak] { display: none; }
</style>
