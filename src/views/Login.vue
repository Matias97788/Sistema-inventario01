<template>
  <v-app id="inspire">
    <v-content>
      <v-container
        class="fill-height"
        
        fluid
      >
        <v-row
          align="center"
          justify="center"
        >
          <v-col
            cols="12"
            sm="8"
            md="6"
            class="text-center"
          >
            <v-card class="elevation-12"
             :height="350">
              <v-toolbar
                color="primary"
                dark
                flat
              >
                <v-toolbar-title>Inicio session </v-toolbar-title>
                <v-spacer />
              
              
              </v-toolbar>
              <v-card-text class="mt-6"
              >
                <v-form  @submit.prevent="login">
                  <v-text-field
                    label="Login"
                    name="login"
                    prepend-icon="account_circle"
                    type="text"
                    v-model="usuario"
                  />

                  <v-text-field
                    id="password"
                    label="Password"
                    name="password"
                    prepend-icon="vpn_key"
                    type="password"
                    v-model="clave"
                  />
                   <v-select
                    width="100"
                    label="Seleccione un liceo"
                    dense
                  ></v-select>
                  <v-btn type="submit" color="primary" block>Login</v-btn>

                </v-form>
                 <!-- <v-alert :type ="alert.type">
                 {{alert.text}}
                </v-alert> -->
              </v-card-text>
            
            </v-card>
          </v-col>
        </v-row>
    
      </v-container>
    </v-content>
   
  </v-app>
</template>

<script>
import firebase from 'firebase';
  export default {
     data() {
      return{
          clave:"",
          usuario:"",
          // alert:{ type:"error", text:"Anonimo"}

      }
    },
    props: {
      
      source: String,
    },
    methods:{
        login(){
            firebase
            .auth()
            .signInWithEmailAndPassword(this.usuario, this.clave)
            // eslint-disable-next-line no-unused-vars
            .then((user)=>   
          //   this.alert.type = "success",
          // this.alert.text = user.user.email,
            this.$router.replace('home'),
          
            
            (error) => console.error(error));
            
           
        }
    }
  }
</script>