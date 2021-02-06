<template>
  <div>
    <!--<p>{{ $t("hello", {name}) }}</p>
    <p>{{ $t("goodbye") }}</p>
    
    <p>{{ $tc("person", 0)}}</p>
    <p>{{ $tc("person", 1)}}</p>
    <p>{{ $tc("person", 4)}}</p> -->

    <!--<p>{{ $d(new Date(), "long") }}</p>
    <p>{{ $d(new Date(), "long", "en-GB") }}</p> -->

    <!--<p>{{ product.name }}: {{ $n(product.price, 'currency') }}</p>
    <p>{{product.stock}} left in stock</p> -->

    <!--<p>
      <i18n-n :value="4005.45" format="currency">
        <template v-slot:currency="slotProps">
          <span style="color: red; font-weight: bold;">{{ slotProps.currency }}</span>
        </template>
        <template v-slot:integer="slotProps">
          <span style="color: green;">{{ slotProps.integer }}</span>
        </template>
        <template v-slot:decimal="slotProps">
          <span style="color: blue;">{{ slotProps.decimal }}</span>
        </template>
        <template v-slot:fraction="slotProps">
          <span style="color: orange;">{{ slotProps.fraction }}</span>
        </template>
        <template v-slot:group="slotProps">
          <span style="color: green; font-size: 25px;">{{ slotProps.group }}</span> // Styles the comma / point
        </template>
      </i18n-n>
    </p> -->

    <i18n path="terms" tag="p">
      <template v-slot:termsUrl>
        <a href="/terms">{{$t("termsLink")}}</a>
        <!-- <button @click="openModal">{{ $t("termsLink") }}</button> // Just an idea from the author to open the terms and conditions in a modal instead of a new page -->
      </template>        
    </i18n>

    <button @click="setLocale('en-GB')" class="button">UK</button>
    <button @click="setLocale('en-US')" class="button">USA</button>
    <button @click="setLocale('es')" class="button">Spain</button>
  </div>
</template>

<script>
const products = {
  "en-US": {
    name: 'Red Jeans',
    stock: 4,
    price: 89
  },
  "en-GB": {
    name: 'Red Jeans',
    stock: 14,
    price: 104
  },
  "es-ES": {
    name: 'Vaqueros Rojos',
    stock: 109,
    price: 50
  },
}; 

export default {
  name: "HelloI18n",
  data() {
    return {
      name: 'Debii'
    }
  },
  methods: {
    setLocale(locale) {
      this.$i18n.locale = locale;
      localStorage.setItem("locale", locale);
    }
  },
  computed: {
    product() {
      return products[this.$i18n.locale]
    }
  }
};
</script>