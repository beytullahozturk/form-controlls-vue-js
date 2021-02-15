<template>
  <div class="container">
    <form v-if="!isSubmit">
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
          <div class="panel panel-info">
            <div class="panel-heading">
              <h4>Kayıt Formu</h4>
            </div>
            <div class="panel-body">
              <appFullname v-model="fullname"></appFullname>
              <label for="email">Email</label>
                <input type="text" id="email" class="form-control" placeholder="email adresiniz" v-model="mail">
              <label for="password">Parola</label>
                <input type="password" id="password" class="form-control" v-model="password">
              <label for="cinsiyet">Cinsiyet</label>
              <div>
                <label>
                  <input v-model="gender" type="radio" value="Erkek"> Erkek
                </label>
                <label>
                  <input v-model="gender" type="radio" value="Kadın"> Kadın
                </label>
              </div>
              <div class="action">
                <button class="btn btn-primary btn-block" @click.prevent="submit">Kaydet</button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </form>
    <div class="row" v-if="isSubmit" v-else>
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <div class="panel panel-info">
          <div class="panel-heading">
            <h4>Girdiğiniz Bilgier</h4>
          </div>
          <div class="panel-body">
            <p><strong>Tam Ad:</strong> {{ fullname }} </p>
            <p><strong>E-mail:</strong> {{ mail }} </p>
            <p><strong>Şifre:</strong> {{ password }} </p>
            <p><strong>Cinsiyet:</strong> {{ gender }} </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import FullName from "./FullName";
  export default {
    components:{
      appFullname : FullName,
    },
    data(){
      return{
        fullname:'',
        mail:'',
        password:'',
        gender:'',
        isSubmit:false
      }
    },
    methods:{
      submit(){
        this.isSubmit= true
      }
    }
  }
</script>

<style>
.action{
  margin-top: 20px;
}
.container{
  margin-top: 10px;
}
</style>
