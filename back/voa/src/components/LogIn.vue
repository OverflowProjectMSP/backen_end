<script>
import axios from 'axios';
import { vModelCheckbox } from 'vue';
axios.defaults.withCredentials = true;
export default {
    data(){
        return {
            form: {
                user: '',
                password: ''
            }
        }
    },
    methods:{
        async LogIn(){
            let response = await fetch(
            'http://127.0.0.1:5000/login',{
                method: 'POST',
                mode: 'cors',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify(this.form),
                credentials: "include"
                }).then((data) => {
                if (data.ok){
                    return data.json()
                } else{ 
                    console.error('HTTP status: '+ data.status)
                }
                console.log(data)
            })
        },

    },
}
</script>


<template>
    <div class="container">
            <div class="row pt-5">
                <div class="col-3 ">
                    <h3>Войти</h3>
                </div>
            </div>
            <hr>
            <div class="row">
                <div class="col-12">
                    <h5>Ведите почту</h5>
                    <div class="input-group mb-3">
                        <input type="text" class="form-control" placeholder="exemple.mail@mail.ru" aria-label="Secondname" v-model="form.user" aria-describedby="basic-addon1">
                    </div>
                </div>
            </div>
            <div class="row">
                <div class="col-12">
                    <h5>Введите пароль</h5>
                    <div class="input-group mb-3">
                        <input type="text" class="form-control" placeholder="*************" aria-label="Secondname" v-model="form.password"
                            aria-describedby="basic-addon1">
                    </div>
                </div>
            </div>
            <div class="row pt-5">
                <div class="col-4">
                    <button class="save" @click="LogIn()"><b>Войти</b></button>
                </div>
            </div>
        </div>
    
</template>



<style>
.save{
    background-color: white;
    color: #7ac97a;
    border-color: #90EE90;
    border-radius: 5px;
    padding-right: 15px;
    padding-left: 15px;
    text-align: center;
}
.container{
    padding: 0 20%;
}

</style>