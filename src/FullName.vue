<template>
  <div>
    <label for="firstName">Ad</label>
    <input type="text" class="form-control" placeholder="adınız" :value="firstName" @input="nameChanged(true, $event)">
    <label for="lastName">Soyad</label>
    <input type="text" class="form-control" placeholder="soyadınız" :value="lastName" @input="nameChanged(false, $event)">
  </div>
</template>

<script>
export default {
  props : ["value"],
  computed : {
    firstName(){
      return this.value.split(" ")[0];
    },
    lastName(){
      return this.value.split(" ")[1];
    }
  },
  methods : {
    nameChanged(isFirst, event){
      let fullName = "";
      if(isFirst){
        fullName = event.target.value + ' ' + this.lastName;
      } else {
        fullName = this.firstName + ' ' + event.target.value;
      }
      this.value = fullName;
      this.$emit("input", this.value)
    }
  }
}
</script>