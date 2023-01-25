<template>
    <v-row>
      <v-col cols="10" offset="1" md="4" offset-md="4">
        <v-card>
            <v-toolbar color="primary" dark>Register</v-toolbar>
            <v-card-text>
                <v-form>
                    <v-text-field
                        label="Name"
                        required
                        v-model="form.fullname"
                        :rules="rules.fullname"
                    />
                    <v-text-field
                        label="Email"
                        required
                        v-model="form.email"
                        :rules="rules.email"
                    />
                    <v-text-field
                        label="Pasword"
                        type="password"
                        required
                        v-model="form.password"
                        :rules="rules.password"
                    />
                    <v-text-field
                        label="Confirm Pasword"
                        type="password"
                        required
                        v-model="form.password_confirm"
                        :rules="rules.password_confirm"
                    />
                </v-form>
            </v-card-text>

            <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn color="primary">Register</v-btn>
            </v-card-actions>

        </v-card>

        <div class="d-flex align-baseline">
            <p>Sudah mempunyai akun?</p>
            <v-btn
                text
                plain
                :ripple="false"
                color="primary"
                to="/login"
                class="pl-1"
            >Login</v-btn>
        </div>
      </v-col>
    </v-row>
  </template>
  
  <script>
  export default {
    layout: 'auth',
    data() {
        return {
            form: {
                fullname: '',
                email: '',
                password: '',
                password_confirm: ''
            },
            rules: {
                fullname: [
                    v => !!v || 'Name is required',
                ],
                email: [
                v => !!v || 'E-mail is required',
                v => /[a-z0-9]+@[a-z]+\.[a-z]{2,3}/.test(v) || 'E-mail must be valid',
                ],
                password: [
                    v => !!v || 'Password is required',
                    v => v.length >= 8 || 'Password must be at least 8 characters'
                ],
                password_confirm: [
                    v => !!v || 'Password confirm is required',
                    v => v === this.form.password || 'Password confirmation must be same with password'
                ],
            }
        }
    }
  }
  </script>
  