<template>
  <div class="main-content">
    <aside class="content-navigation">
      <slot name="nav"></slot>
    </aside>
    <section v-if="$slots.info" class="subject-info">
      <slot name="info"></slot>
    </section>
    <section v-if="$slots.content" class="content-info">
      <slot name="content"></slot>
    </section>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
main div.main-content {
  display: flex;
}

main div.main-content .content-navigation {
  width: 20%;
  border-right: 3px solid whitesmoke;
  border-left: 3px solid whitesmoke;
}

main div.main-content .subject-info {
  padding: 1%;
}

main div.main-content .subject-info p {
  font-size: 18px;
}

main .main-content .content-navigation ul {
  margin: 0;
  padding: 0;
}

main div.main-content .content-navigation ul li {
  list-style-type: none;
  padding: 10%;
  font-size: 23px;
  cursor: pointer;
  text-align: left;
}

main div.main-content .content-navigation ul li:hover {
  background: whitesmoke;
}

main div.main-content .content-navigation ul li:active {
  border-right: 5px solid #44a9f8;
}

main div.main-content .content-navigation ul li.active {
  border-right: 5px solid #44a9f8;
}

main div.main-content .content-navigation ul li a {
  color: black;
  text-decoration: none;
}

main .content-info {
  width: 80%;
  padding: 1%;
  font-size: 18px;
  display: block;
}

main .content-info .user-form input {
  padding: 1%;
  width: 25%;
  border: none;
  border-bottom: 1px solid black;
  font-size: 16px;
  font-family: inherit;
}

main .content-info .user-form input:focus {
  background: rgb(255, 248, 198);
}

main .content-info .user-form .form-group {
  margin-bottom: 1%;
}

main .content-info .user-form .form-group img {
  vertical-align: bottom;
}

main .content-info .user-form button {
  padding: 1%;
  background: #44a9f8;
  color: white;
  border: none;
  width: 10%;
  font-size: 16px;
  cursor: pointer;
}

main .content-info .user-links a {
  color: black;
  text-decoration: none;
  font-weight: normal;
  margin: 2%;
}

main .content-info .user-links a:hover {
  color: #44a9f8;
  text-decoration: underline;
}

main .content-info .user-links .active-route {
  color: #44a9f8;
  text-decoration: underline;
}

div.form-group {
  margin-top: 1%;
  margin-bottom: 1%;
}

.btn {
  padding: 1%;
  background: #44a9f8;
  color: white;
  border: none;
  width: 10%;
  font-size: 16px;
  cursor: pointer;
  border: 1px solid white;
  display: block;
  margin: 0 auto;
  margin-top: 1%;
  margin-bottom: 1%;
}

.btn:hover {
  color: #44a9f8;
  background: white;
  border: 1px solid #44a9f8;
  text-decoration: underline;
}
</style>