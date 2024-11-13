<template>
    <input type="text" v-model="userName" placeholder="Имя">
    <input type="password" v-model="userPass" placeholder="Пароль">
    <input type="email" v-model="userEmail" placeholder="EMail">

    <p className="error">{{ error }}</p>

    <button @click="sendData()">Отправвить</button>

    <div v-if="users.length == 0" className="user">
        У нас нет пользователей
    </div>
    <div v-else-if="users.length == 1" className="user">
        У нас всего ОДИН пользователь
    </div>
    <div v-else className="user">
        Все остальное
    </div>

    <User v-for="(el, index) in users" :key="index" :user="el" :index="index" :deleteUser="deleteUser" />
    
    <!-- <p>{{ userName }}</p> -->
    <!-- <p>{{ userPass }}</p> -->
    <!-- <p>{{ userEmail }}</p> -->
</template>


<script>
    import User from './components/User.vue'

    export default {
        components: { User },

        data() {
            return {
                users: [],
                error: '',
                userName: '',
                userPass: '',
                userEmail: ''
            }
        },

        methods: {
            sendData() {
                
                if(this.userName == '') {
                    this.error = 'Имя не введено';
                    return;
                } else if(this.userPass == '') {
                    this.error = 'Пароль не введен';
                    return;
                } else if(this.userEmail == '') {
                    this.error = 'EMail не введен';
                    return;
                }

                this.error = '';


                this.users.push({
                    name: this.userName,
                    pass: this.userPass,
                    email: this.userEmail
                })
            },

            deleteUser(index) {
                this.users.splice(index, 1);
            }
        }
    }
</script>


<style scoped>
    input {
        display: block;
        margin-bottom: 10px;
        border-radius: 3px;
        border: 1px solid silver;
        outline: none;
        padding: 10px 15px;
        background: #fafafa;
        color:#333;
    }
    
    button {
        border: 0;
        border-radius: 5px;
        outline: none;
        padding: 10px 15px;
        background: #6cd670;
        color: #167f3d;
        font-weight: bold;
        cursor: pointer;
        transition: transform 500ms ease;
    }

    button:hover {
        transform: translateY(-5px);
    }

    .user {
        width: 500px;
        margin-top: 20px;
        border: 1px solid silver;
        background: #e3e3e3;
        color: #222;
        padding: 20px;
        border-radius: 5px;
    }
</style>
