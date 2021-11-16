<template>
  <div class="container">
    <form v-on:submit.prevent="submitForm">
      <div class="form-group">
        <label for="fname">First Name</label>
        <input
          type="text"
          class="form-control"
          id="fname"
          placeholder="First Name"
          v-model="form.fname"
        />
      </div>
      <div class="form-group">
        <label for="lname">Last Name</label>
        <input
          type="text"
          class="form-control"
          id="fname"
          placeholder="Last Name"
          v-model="form.lname"
        />
      </div>
      <div class="form-group">
        <label for="exampleInputEmail1" class="required">Email address</label>
        <input
          type="email"
          class="form-control"
          id="exampleInputEmail1"
          placeholder="Enter email"
          v-model="form.email"
          required
        />
      </div>
      <div class="form-group">
        <label for="subject" class="required">Subject</label>
        <textarea
          class="form-control"
          id="subject"
          rows="1"
          placeholder="Please write your subject"
          v-model="form.subject"
          required
        ></textarea>
      </div>
      <div class="form-group">
        <label for="message">Message</label>
        <textarea
          class="form-control"
          id="message"
          rows="3"
          placeholder="Please write your message"
          v-model="form.message"
        ></textarea>
      </div>
      <button type="submit" class="btn btn-primary" value="submit">
        Submit
      </button>
      <button type="button" class="btn btn-primary" v-on:click="exportData">
        <i class="fa fa-download" aria-hidden="true"></i>
        Submitted data in JSON format
      </button>
    </form>
    <br />

    <div v-if="dataSubmitted">
      <p class="alert alert-success" role="alert">
        Form submitted successfully
      </p>
    </div>

    <div v-if="exportButtonClicked">
      <div v-if="dataSubmitted">
        <p class="alert alert-success" role="alert">
          JSON file downloaded successfully
        </p>
      </div>
      <div v-else>
        <p class="alert alert-warning" role="alert">
          {{ this.error }}
        </p>
      </div>
    </div>
  </div>
</template>
<script>
import axios from "axios";

export default {
  name: "contact",
  components: {},
  data() {
    return {
      form: {
        fname: "",
        lname: "",
        email: "",
        subject: "",
        message: "",
      },
      dataSubmitted: false,
      exportdata: null,
      exportButtonClicked: false,
      error: "",
    };
  },
  methods: {
    submitForm() {
      /*axios
        .post("https://exam.candy-dev.com/wp-json/wp/contact", this.form)
        .then((res) => {
          
        })
        .catch((error) => {
          
        })
        .finally(() => {
          
        });   
    */
      this.exportButtonClicked = false;
      this.dataSubmitted = true;
      console.log("Submitted", this.form);
    },
    exportData() {
      this.exportButtonClicked = true;
      if (this.dataSubmitted) {
        this.exportdata = JSON.stringify(this.form, null, 2);
        const blob = new Blob([this.exportdata], { type: "text/plain" });
        const e = document.createEvent("MouseEvents"),
          a = document.createElement("a");
        a.download = "submittedFormData.json";
        a.href = window.URL.createObjectURL(blob);
        a.dataset.downloadurl = ["text/json", a.download, a.href].join(":");
        e.initEvent(
          "click",
          true,
          false,
          window,
          0,
          0,
          0,
          0,
          0,
          false,
          false,
          false,
          false,
          0,
          null
        );
        a.dispatchEvent(e);
      } else {
        this.error = "Please submit the form before exporting JSON";
      }
      //this.exportButtonClicked = false;
    },
  },
};
</script>
<style scoped>
@import 'https://pro.fontawesome.com/releases/v5.10.0/css/all.css';

.required:after {
  content: "* ";
  color: red;
}
</style>
