<template>
  <div class="container">
    <div>
      <h1>{{ teaName }}</h1>
    </div>
    <div>
      <form
        name="vue-tea"
        method="post"
        data-netlify="true"
        data-netlify-honeypot="bot-field"
      >
        <input type="hidden" name="form-name" value="vue-tea" />
        <div class="tea">
          <h2>Pick a Tea</h2>
          <label
            v-for="tea in teaNames"
            :key="tea"
            :class="{
              'tea-label': true,
              checked: tea === chosenTea
            }"
          >
            <input
              id="tea"
              v-model="chosenTea"
              name="tea"
              type="radio"
              :value="tea"
            />
            <span>{{ tea }}</span>
          </label>
        </div>
        <button>Submit</button>
      </form>
    </div>

    <h2>HTML Forms</h2>
    <form
      name="name-form"
      method="post"
      data-netlify="true"
      data-netlify-honeypot="bot-field"
    >
      <label for="fname">First name:</label><br />
      <input id="fname" type="text" name="fname" value="John" /><br />
      <label for="lname">Last name:</label><br />
      <input id="lname" type="text" name="lname" value="Doe" /><br /><br />
      <button>Submit</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      chosenTea: 'Earl Grey',
      teaTypes: {
        'Earl Grey': 'London',
        'Irish Breakfast': 'Dublin',
        Chai: 'Bombay',
        Rose: 'Atlantic City',
        Matcha: 'Tokyo',
        Rooibos: 'Cape Town',
        'Yerba Mate': 'Montreal',
        Green: 'Oregon Mist'
      }
    }
  },
  computed: {
    teaName() {
      return `${this.teaTypes[this.chosenTea]} Fog`
    },
    teaNames() {
      return Object.keys(this.teaTypes)
    }
  }
}
</script>

<style>
.container {
  padding: 10px;
}
</style>
