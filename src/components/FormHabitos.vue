<template>
  <div class="q-pa-md">
    <h3>Habitos</h3>
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
      
      <button @click="setData">Continue</button>
      <button @click="volver">Back</button>
    </form>
  </div>
</template>


<script>
export default {
  name: "FormHabitos",
  data () {
    return {
      name: null,

      step: 2,
    }
  },

  methods: {
    setData() {
      this.$refs.name.validate()

      if (this.$refs.name.hasError) {
        console.log("Error en el Form");
      }else{
        this.step++;
        console.log(this.step);
        this.$emit("getData",this.step);
      }
      },
      volver(){
        this.step = 1;
        this.$emit("getData",this.step);
      }
    }
}
</script>
