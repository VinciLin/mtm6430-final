<template>
    <div>
        <form @submit.prevent="onSubmit" class="text-center bg-primary text-white rounded">
            <h1>Sign In</h1>
            <div class="row">
                <div class="col-6">
                    <label for="email">Email</label>
                    <input type="email" v-model="email" id="email" requried />
                </div>
                <div class="col-6">
                    <label for="pass">Password</label>
                    <input type="password" v-model="pass" id="pass" requried />
                </div>
            </div>
             <br>
            <button type="submit" class="btn btn-warning">Submit</button>
        </form>


    </div>
</template>
<script>
import { mapActions } from "vuex";
    export default {
        data() {
            return {
                email: "",
                pass: ""
            };
        },

        methods: {
            ...mapActions(["signIn"]),
            onSubmit() {
            const formData = {
                email: this.email,
                password: this.pass
            };

            this.signIn(formData);
            }
        }
    };
</script>

<style>

h1 {
    text-align: center;
    padding-bottom: 2rem;
}
form {
    padding: 2rem;
    box-shadow: 0 14px 28px rgba(0,0,0,0.25), 0 10px 10px rgba(0,0,0,0.22);
    max-width: 30rem;
    margin: 0 auto;
}

label {
    display: block;
}

input,
button {
    padding: 5px 10px;
    margin: 10px 0;
}

</style>