<template>
  <h1>
    Braintree Demo
  </h1>

  <div id="dropin-container"></div>
</template>

<script>
export default {
  name: "Home",
  data: () => ({
    //......data of your component
  }),

  mounted() {
    //let braintreeScript = document.createElement("script");
    var braintreeScript = require('braintree-web-drop-in')

      console.log("BT Loaded");

      var button = document.querySelector("#submit-button");

      braintreeScript.create(
        {
          authorization: "sandbox_g42y39zw_348pk9cgf3bgyw2b",
          selector: "#dropin-container",
        },
        function(err, instance) {
          button.addEventListener("click", function() {
            instance.requestPaymentMethod(function(err, payload) {
              // Submit payload.nonce to your server
              console.log(err);
              console.log(payload);
            });
          });
        }
      );

    braintreeScript.onload = () => {

    };

    document.head.appendChild(braintreeScript);
  },

  methods: {
    //  ......methods of your component
  },
};
</script>
