<template>
  <div>
    <NavBar />

    <div class="container">
      <div class="card">
        <div class="card-header">
          <h1>Welcome to our Library</h1>
        </div>
        <div class="card-body">
          <blockquote class="blockquote mb-0">
            <p>“The more that you read, the more things you will know. The more that you learn, the more places you’ll go.”</p>
            <footer class="blockquote-footer"> Dr.  Seus</footer>
          </blockquote>
        </div>      
        <div class="card-body">
          <a class="btn btn-primary btn-lg btn-block" href="/register" role="button">Register</a>
          <a class="btn btn-primary btn-lg btn-block" href="/login" role="button">Login</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  auth: false
}
</script>
<style scoped>
.card{
  margin: 20px;
  margin-top: 50px;
}
</style>