<template>
 
  <div class="dashboard">
    <h1 class="subheading grey--text">Dashboard</h1>


  <v-card>
    <v-toolbar
      color="purple"
      dark
      flat
      prominent
    >
      <v-text-field
        append-icon="mic"
        class="mx-4"
        flat
        hide-details
        label="Search"
        prepend-inner-icon="search"
        solo-inverted
      ></v-text-field>

      <template v-slot:extension>
        <v-tabs
          v-model="tabs"
          centered
        >
          <v-tab
            v-for="n in 3"
            :key="n"
          >
            Item {{ n }}
          </v-tab>
        </v-tabs>
      </template>
    </v-toolbar>

    <v-tabs-items v-model="tabs">
      <v-tab-item>
        <v-card flat>
          <v-card-text>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
          </v-card-text>
        </v-card>
      </v-tab-item>
      <v-tab-item>
        <v-card flat>
          <v-card-title class="headline">An awesome title</v-card-title>
          <v-card-text>
            <p>
              Duis lobortis massa imperdiet quam. Donec vitae orci sed dolor rutrum auctor. Vestibulum facilisis, purus nec pulvinar iaculis, ligula mi congue nunc, vitae euismod ligula urna in dolor. Praesent congue erat at massa.
            </p>

            <p>
              Aenean posuere, tortor sed cursus feugiat, nunc augue blandit nunc, eu sollicitudin urna dolor sagittis lacus. Pellentesque egestas, neque sit amet convallis pulvinar, justo nulla eleifend augue, ac auctor orci leo non est. Etiam sit amet orci eget eros faucibus tincidunt. Donec sodales sagittis magna.
            </p>

            <p class="mb-0">
              Ut leo. Suspendisse potenti. Duis vel nibh at velit scelerisque suscipit. Fusce pharetra convallis urna.
            </p>
          </v-card-text>
        </v-card>
      </v-tab-item>
      <v-tab-item>
        <v-card flat>
          <v-card-title class="headline">An even better title</v-card-title>
          <v-card-text>
            <p>
              Maecenas ullamcorper, dui et placerat feugiat, eros pede varius nisi, condimentum viverra felis nunc et lorem. Sed hendrerit. Maecenas malesuada. Vestibulum ullamcorper mauris at ligula. Proin faucibus arcu quis ante.
            </p>

            <p class="mb-0">
              Etiam vitae tortor. Curabitur ullamcorper ultricies nisi. Sed magna purus, fermentum eu, tincidunt eu, varius ut, felis. Aliquam lobortis. Suspendisse potenti.
            </p>
          </v-card-text>
        </v-card>
      </v-tab-item>
    </v-tabs-items>
  </v-card>







    
    <h1 class="subheading red--text text-center">Payments details</h1>
    <div class="text-center">
    <v-btn rounded color="primary" light
    @click="loadPayments"
    >Load Payments</v-btn>
  </div>
    <v-simple-table fixed-header height="300px">
    <template v-slot:default>
      <thead>
        <tr>
          <th class="text-left">Student_ID</th>
          <th class="text-left">Jan</th>
          <th class="text-left">Feb</th>
          <th class="text-left">Mar</th>
          <th class="text-left">Apr</th>
          <th class="text-left">May</th>
          <th class="text-left">Jun</th>
          <th class="text-left">Jul</th>
          <th class="text-left">Aug</th>
          <th class="text-left">Sept</th>
          <th class="text-left">Oct</th>
          <th class="text-left">Nov</th>
          <th class="text-left">Dec</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="payment in payments" :key="payment.id">
           <td>{{payment.studentID }}</td>
           <td>{{payment.January }}</td>
           <td>{{payment.February }}</td>
           <td>{{payment.March }}</td>
           <td>{{payment.April }}</td>
           <td>{{payment.May }}</td>
           <td>{{payment.June }}</td>
           <td>{{payment.July }}</td>
           <td>{{payment.August }}</td>
           <td>{{payment.September }}</td>
           <td>{{payment.October }}</td>
           <td>{{payment.November }}</td>
           <td>{{payment.December }}</td>

           
    
        </tr>
      </tbody>
    </template>
  </v-simple-table>
   <v-progress-linear value="55"></v-progress-linear>
    <h1 class="subheading red--text text-center">Students</h1>
    <div class="text-center">
    <v-btn rounded color="primary" light
    @click="loadDetails"
    >Load 2017 students</v-btn>
  </div>
    
    <v-simple-table fixed-header height="300px">
    <template v-slot:default>
      <thead>
        <tr>
          <th class="text-left">First Name</th>
          <!-- <th class="text-left">Last Name</th> -->
          <th class="text-left">Student_ID</th>
          <!-- <th class="text-left">Major</th> -->
          <th class="text-left">Total amt paid</th>
          <th class="text-left">Topup</th>
          <th class="text-left">Subtract</th>

        </tr>
      </thead>
      <tbody>
        <tr v-for="student in students" :key="student.major">
          <td>{{student.firstName}}</td>
          <!-- <td>{{student.lastName}}</td> -->
          <td> {{student.studentID}}</td>
          <!-- <td>{{student.major}}</td> -->
          <td>{{student.payment}}</td>
          <td> 
              <v-btn class="mx-2" fab dark color="indigo"
             
              >
      <v-icon dark>mdi-plus</v-icon>
            </v-btn>
          </td>
          <td><v-btn class="mx-2" fab dark small color="primary">
      <v-icon dark>mdi-minus</v-icon>
    </v-btn></td>
          
        </tr>
      </tbody>
      <h1 class="danger">tyftfty</h1>
    </template>
  </v-simple-table>

     
  </div>
</template>

<script>
export default {
  data() {
    return {
      
      students:[],
      payments:[],
      tabs: null,
      text: 'Lorem ipsu'
       
    };
  },
  methods: {
    loadPayments(){
      this.$http.get('https://fundapi.herokuapp.com/v1/payments/')
                .then(resp=>{
                  return resp.json()
                  /* eslint-disable */
                }).then(data =>{
                  const pay =[];
                  for(let key in data){
                    pay.push(data[key]);
                  }
                  this.payments = pay;

                });
            

    },
    loadDetails(){
      this.$http.get('https://fundapi.herokuapp.com/v1/payments/')
                  .then(response=>{
                    return response.json();
                    /* eslint-disable */
                  })
                  .then(data=> {
                    const studentsRecieved =[];
                    for(let key in data){
                      studentsRecieved.push(data[key]);
                    }
                    this.students = studentsRecieved;
                    
                  });         

    },
    addPayment(studentID){
      this.$http.get(`https://fundapi.herokuapp.com/v1/student/${studentID}.json`)
      

    },
    sortBy(prop) {
      this.projects.sort((a, b) => (a[prop] < b[prop] ? -1 : 1));
    }
  }
};
</script>

<style>
.project.complete {
  border-left: 4px solid #3cd1c2;
}
.project.ongoing {
  border-left: 4px solid orange;
}
.project.overdue {
  border-left: 4px solid tomato;
}
.v-chip.complete {
  background: #3cd1c2 !important;
}
.v-chip.ongoing {
  background: #ffaa2c !important;
}
.v-chip.overdue {
  background: #f83e70 !important;
}
</style>