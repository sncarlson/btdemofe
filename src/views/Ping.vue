<template>
  <div class="ping">
    <h1>GraphQL API Ping results:</h1>
    <p>
      Respone from "ping": {{rails.ping}}.
    </p>
    <p>
      Request ID: {{rails.request_id}}
    </p>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Ping",
  data() {
    return {
      rails: {},
    };
  },

  created() {
    axios
      .get("http://localhost:3000/ping")
      .then((response) => (this.$data.rails = response.data))
      .catch((e) => {
        this.errors.push(e);
      });
  },

  methods: {
    //  ......methods of your component
  },
};
</script>
