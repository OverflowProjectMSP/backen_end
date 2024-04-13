<script>


export default {
  data() {
    return {
      form:{
        name: '',
        email: '',
        password: ''
      }
    }
  },
  methods: {
    async addUser(){
      let response = await fetch(
        'http://127.0.0.1:5000/registration',{
          method: 'POST',
          mode: 'cors',
          headers: {
            'Content-Type': 'application/json',
          },
          body: JSON.stringify(this.form),
          credentials: "same-origin"
        }).then((data) => {
        if (data.ok){
          return data.json()
        } else{ 
          console.error('HTTP status: '+ data.status)
        }
        console.log(data)
      })
    }
  }
}
</script>


<template>
  <div class="head">
    <h1>Регистрация</h1>
    <hr>
  </div>
  
  <div class="content">
      
    <div class="mb-3 nickname form">
      <label for="exampleFormControlInput1" class="form-label">Введите никнейм</label>
      <input type="text" class="form-control" id="exampleFormControlInput1"  v-model="form.name" placeholder="Никнейм">
    </div>

   <div class="mb-3 emal form">
      <label for="exampleFormControlInput1" class="form-label">Введите почту</label>
      <input type="text" class="form-control" id="exampleFormControlInput1"  v-model="form.email"placeholder="name@example.com">
    </div>

    <div class="mb-3 pasword form">
      <label for="exampleFormControlInput1" class="form-label">Введите пароль</label>
      <input type="text" class="form-control" id="exampleFormControlInput1"  v-model="form.password" placeholder="Пароль">

      <div class="buttons">
        <button class="login-in" @click="addUser">Зарегистрироваться</button>
        <button class="account">Уже есть аккаунт</button>
      </div>
    </div>
  </div>
</template>



<style scoped>
@import url('https://fonts.cdnfonts.com/css/rubik');
html, template, label, .cont {
    font-family: 'rubik';
}
#app {
    font-family: 'rubik';
}
hr{
  display: inline-block;
  text-align: right;
}
.content{
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    width: 500px;
    padding: 20px;
}
.form{
   width: 100%;
}
.head hr {
  width: 65%;
}
.head{
  margin-left: 20px;
  width: 50%;
  margin-top: 10px;
}
.form-control{
  border-radius: 10px;
  height: 30px;
}
.login-in{
  border: solid 1px green;
  margin: 5px;
  border-radius: 7px;
  background-color: white;
  color: green;
  margin-top: 10px;
}
.account{
  border: solid 1px green;
  margin: 5px;
  border-radius: 7px;
  background-color: white;
  color: green;
  margin-top: 10px;
}
</style>