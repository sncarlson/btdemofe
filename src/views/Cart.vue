<template>
  <h1>
    Braintree Demo
  </h1>

  <form id="payment-form" action="/cart" method="post">
    <label for="amount">Amount: </label>
    <input type="tel" id="amount" name="amount" />
    <div id="dropin-container"></div>
    <button type="button" class="btn btn-primary" id="submit-button">
      Request payment method
    </button>
  </form>
</template>

<script>
export default {
  name: "Cart",
  data: () => ({
    //......data of your component
  }),

  mounted() {
    var braintreeScript = require("braintree-web-drop-in");
    var button = document.querySelector("#submit-button");

    braintreeScript.create(
      {
        authorization: "sandbox_rzvmrmvf_rqqznxqr9hxgzr2s",
        container: "#dropin-container",
        card: {
          cardholderName: {
            required: true,
          },
        },
        paypal: {
          flow: "vault",
        },
      },
      function(createErr, instance) {
        button.addEventListener("click", function() {
          instance.requestPaymentMethod(function(
            requestPaymentMethodErr,
            payload
          ) {
            // Submit payload.nonce to your server
            console.log(requestPaymentMethodErr);
            console.log(payload);
          });
        });
      }
    );
  },

  methods: {
    //  ......methods of your component
  },
};
</script>
