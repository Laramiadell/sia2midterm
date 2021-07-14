<template>
    <div>
        <NavBar />

        <div class="container">
            <div class="row">
                <div class="col-md-4 offset-md-4 mt-3">
                    <b-card class="header" header="User Login">
                        <form action="#" @submit.prevent="onLogin">
                            <div class="form-group">
                                <label for="email">Email:</label>
                                <input type="email" v-model="creds.email" id="email" class="form-control">
                            </div>
                            <div class="form-group">
                                <label for="password">Password:</label>
                                <input type="password" v-model="creds.password" id="password" class="form-control">
                            </div>
                            <div class="form-group">
                                <button class="btn btn-primary btn-lg btn-block">Login</button>
                            </div>
                        </form>
                    </b-card>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            creds: {}
        }
    },
    methods: {
        async onLogin() {
            await this.$auth.loginWith('local', {data:this.creds})
            .then((res)=>{
                
            })
            .catch((err)=>{
                alert('Invalid email or password')
            })
        }
    }
}
</script>
<style scoped>
.header{
    font-weight: bold;
}
.row{
    margin-top: 30px;
}
</style>
