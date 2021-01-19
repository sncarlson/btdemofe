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
    let braintreeScript = document.createElement("script");
    braintreeScript.setAttribute(
      "src",
      "https://js.braintreegateway.com/web/dropin/1.25.0/js/dropin.min.js"
    );
    braintreeScript.onload = () => {
      console.log("BT Loaded");

      var button = document.querySelector("#submit-button");

      braintreeScript.dropin.create(
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
    };

    document.head.appendChild(braintreeScript);
  },

  methods: {
    //  ......methods of your component
  },
};
</script>
