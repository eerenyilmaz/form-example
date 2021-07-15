<template>
  <div class="container">
    <h3 style="text-align: center">Form Example</h3>
    <hr>
    <div class="row">
      <div class="col-md-6">
        <div class="main-div">
          <div class="header-div">
            <h4>Application Form</h4>
          </div>
          <div class="panel-body">
            <form>
              <div class="row">
                <div class="col-md-12">
                  <div class="form-group">
                    <label for="email">E-Mail</label>
                    <input type="text"
                           id="email"
                           class="form-control"
                           :value="userData.username"
                            @input="userData.username = $event.target.value"
                           required
                    >
                  </div>
                  <div class="form-group">
                    <label for="password">Password</label>
                    <input type="password"
                           id="password"
                           class="form-control"
                           v-model.lazy.trim="userData.password" required>
                  </div>
                  <div class="form-group">
                    <label for="age">Age</label>
                    <input type="number"
                           id="age"
                           class="form-control"
                           v-model.number.trim="userData.age"
                           required>
                  </div>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12 form-group">
                  <label for="message">Description</label><br>
                  <textarea
                    v-model="userData.message"
                    id="message"
                    rows="3"
                    class="form-control"></textarea>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12">
                  <div class="form-group">
                    <label>
                      <input v-model="userData.interests" type="checkbox" value="Software"> Software
                    </label>
                    <label>
                      <input v-model="userData.interests" type="checkbox" value="IT"> IT
                    </label>
                  </div>

                </div>
              </div>
              <div class="row">
                <div class="col-md-12 form-group">
                  <label>
                    <input v-model="userData.gender" type="radio" value="Male"> Male
                  </label>
                  <label>
                    <input v-model="userData.gender" type="radio" value="Female"> Female
                  </label>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12 from-group">
                  <label>City</label>
                  <select v-model="userData.selectedCity" class="form-control">
                    <option
                      :selected="city == 'Ankara'"
                      v-for="city in userData.cities">{{ city }}</option>
                  </select>
                </div>
              </div>
              <hr>
              <div class="row">
                <div class="col-md-12">
                  <button
                    @click.prevent="submit"
                    class="submit-btn">Submit!
                  </button>
                </div>
              </div>
            </form>
          </div>
        </div>
      </div>
      <div class="col-md-6" v-if="isSubmitted">
        <div class="panel panel-info">
          <div class="panel-heading">
            <h4>Form Data</h4>
          </div>
          <div class="panel-body">
            <p><strong>Username : </strong> {{ userData.username }}</p>
            <p><strong>Password :</strong> {{ userData.password }}</p>
            <p><strong>Age:</strong> {{ userData.age }}</p>
            <p style="white-space: pre"><strong>Description :</strong> {{ userData.message}} </p>
            <p><strong>Interests :</strong></p>
            <ul>
              <li v-for="item in userData.interests"> {{ item }}</li>
            </ul>
            <p><strong>Gender :</strong> {{ userData.gender}}</p>
            <p><strong>City :</strong> {{ userData.selectedCity}}</p>

          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
export default {
  data(){
    return{
      userData : {
        username : '',
        password : '',
        age : null,
        message :"",
        interests : [],
        gender : '',
        cities : ["İstanbul", "Ankara", "İzmir", "Bursa", "Kocaeli", "Sivas"],
        selectedCity : '',
      },
      isSubmitted : false
    }
  },
  methods : {
    submit : function (){
        this.isSubmitted  = true;
    }
  }
}
</script>

<style>
.header-div{
  background-color: #00ABDD;
  color: white;
  padding: 25px;
  text-align: center;
}
.main-div{
  background-color: white;
  border: 1px solid #00ABDD;
  border-top: none;
}
.main-div label{
  color :#00ABDD;
  font-family: Arial, sans-serif;
  font-style: normal;
  font-weight: normal;
  font-size: 15px;
}
.submit-btn{
  font-family: Arial,sans-serif;
  color: white;
  background-color: #00ABDD;
  border: none;
  padding: 5px 10px;
  border-radius: 5px;
  width: 100px;
  height: 40px;
}
.panel-body strong{
  color : #31708f
}
.panel-body p{
  color : #31b0d5
}
</style>
