# VueJS Simple Form Wizard
Simple Implementation of Multi Step Form with Validation in Vue 

![alt text](https://github.com/tushargugnani/vue-simple-form-wizard/blob/master/public/images/vue-multi-step-form.gif)

### Template

This is how you can declare a multistep form template in your HTML

```html
<form-wizard>
      <tab name="Step 1" info="Introduction" :selected="true">
       <!-- Step 1 of Form Goes Here-->
      </tab>
      <tab name="Step 2" info="More Details" :selected="true">
      <!-- Step 2 of Form Goes Here-->
     </tab>
     <tab name="Step 3" info="Finishing Up" :selected="true">
     <!-- Step 3 of Form Goes Here-->
    </tab>
</form-wizard>
```


### Form Fields

Here is an example declaration of form-field inside the tab component

```html
<div class="field">
    <label class="label">Name</label>
    <div class="control">
    <input class="input" name="fullname" type="text" placeholder="Text input"  v-model="registration.name" data-vv-scope="step1" v-validate="'required'">
    <p class="help is-danger" v-show="errors.has('step1.fullname')">
         {{ errors.first('step1.fullname') }}
    </p>
   </div>
</div>
```

I am using bulma component and hence some styling classes refer to that. You can use any design framework.

**data-vv-scope** : This is for vee-validate validation, and this defines the step that this tab belongs to. (use step1, step2 etc.)

**data-validation** : Add validation rules as per your requirement.

## Demo

[Working Demo](https://tushargugnani.github.io/vue-simple-form-wizard/)

### Code Explanation

I have written a code explanation on my blog [VueJS Multi-Step Form Wizard](https://www.5balloons.info/simple-multi-step-form-wizard-with-validation-in-vuejs/)
