<template>
    <div class="dashboard">
        <div class="info rounded text-center">
            <h1 class="text-primary">Welcome {{ user.name }}</h1>
            </br><h6>Your log in email is: </br><b> {{ user.email }}</b></h6>
            <h6>Your age is: </br><b> {{ user.age }}</b></h6>
            <h6>Your city is: </br><b> {{user.city }}</b></h6>
            <h6>Your job is: </br><b> {{user.job }}</b></h6>
        </div>
        
        <form @submit.prevent="submitForm" class="text-center bg-primary text-white rounded">
            <h1>Dashboard</h1>
            <h6>You can change your information here: </h6>
            <br/>
            <div class="row">
                <div class="col-6">
                    <label for="name">Edit your name:</label>
                    <input type="text" id="name" v-model="user.name">
                </div>
                <div class="col-6">
                    <label for="city">Edit your city:</label>
                    <input type="text" id="city" v-model="user.city">
                </div>
            </div>

            <div class="row">
                <div class="col-6">
                    <label for="age">Edit your age:</label>
                    <input type="text" id="age" v-model="user.age">
                </div>
                <div class="col-6">
                    <label for="job">Edit your job:</label>
                    <input type="text" id="job" v-model="user.job">
                </div>
            </div>
            <br>
            <button type="submit"  value="Submit" class="btn btn-warning">Submit</button>
            <!-- <input type="submit"  value="Submit" /> -->
        </form>
    </div>
</template>
<script>
import { mapActions, mapGetters } from 'vuex';
export default {
    computed:{
        ...mapGetters({
            userData:"getUser"
        }), 
        user(){
            return !this.userData ? false : this.userData;
        }
    },

    created(){
        this.getUserData();
    },

    methods: {
        ...mapActions(["fetchUser", "updateUser"]),
        submitForm(){
            this.updateUser();
        },

        getUserData(){
            let userEmail = localStorage.getItem("userEmail");
            this.fetchUser(userEmail);  
        },
        
    }
}
</script>

<style>
.info {
    margin: 2rem auto;
    padding: 2rem;
    border: 1px solid black;
    max-width: 30rem;
}
</style>


