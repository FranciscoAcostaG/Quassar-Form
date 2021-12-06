<template>
  <div class="q-pa-md">
    <h3>Datos Personales</h3>
    <form
      class="q-gutter-md col-5"
    >
      <q-input
        ref="name"
        filled
        v-model="name"
        label="Your name *"
        hint="Name and surname"
        lazy-rules
        :rules="[(val) => (val && val.length > 0) || 'Please type something']"
      />

      <q-input
        ref="age"
        filled
        type="number"
        v-model="age"
        label="Your age *"
        lazy-rules
        :rules="[
          (val) => (val !== null && val !== '') || 'Please type your age',
          (val) => (val > 0 && val < 100) || 'Please type a real age',
        ]"
      />

      <button @click="setData">Continue</button>
    </form>
  </div>
</template>


<script>
export default {
  name: "FormSalud",
  data () {
    return {
      name: null,
      age: null,

      step: 1
    }
  },

  methods: {
     setData() {
      this.$refs.name.validate()
      this.$refs.age.validate()

      if (this.$refs.name.hasError || this.$refs.age.hasError) {
        console.log("Error en el Form");
      }else{
        this.step++;
        console.log(this.step);
        this.$emit("getData",this.step);
      }
    },
  }
}
</script>
