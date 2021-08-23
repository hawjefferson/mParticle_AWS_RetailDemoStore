<template>
  <Layout>
    <div class="content">
      <div class="container">
        <h3>Customer Profile Information</h3>

        <!-- Checking backend indicator -->
        <div class="container mb-4" v-if="checkingBackend">
          <i class="fas fa-spinner fa-spin fa-3x"></i>
        </div>

        <!-- Backend NOT configured -->

          <p>This information is retrieved via mParticle's Profile API
          </p>
<!-- <button onclick="myFunction()">Show Profile API Result</button>-->
 
   <p><vue-json-pretty :path="'res'" :data="{ postData }" @click="handleClick"></vue-json-pretty></p>



      </div>
    </div>
  </Layout>
</template>
<script>
import VueJsonPretty from 'vue-json-pretty';
import 'vue-json-pretty/lib/styles.css';

export default {
  name: "post-profile-async-await",
  data() {
    return {
      postData: null
    };
  },
  components: {
    VueJsonPretty,
  },
  async created() {
    // POST request using fetch with async/await
    const requestOptions = {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({ mpid: window.mParticle.Identity.getCurrentUser().getMPID() })
    };
    const response = await fetch("https://mparticle.workflows.okta.com/api/flo/298b2563c234c75c6853d6f37f5182c0/invoke", requestOptions);
    const data = await response.json();
    this.postData = data;
  }
};
</script>


<style scoped>
  #chatBot {
    margin-top: 0px;
    max-height: 95vh;
    overflow-y: auto;
  }

  .card-recommend {
    min-width: 250px;
  }

  .error {
    margin-bottom: 150px;
  }
  

   
</style>