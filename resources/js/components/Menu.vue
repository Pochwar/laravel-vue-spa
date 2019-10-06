<template>
  <nav id="nav">
    <ul>
      <!--UNLOGGED-->
      <li v-if="!$auth.check()" v-for="(route, key) in routes.unlogged" v-bind:key="route.path">
        <router-link  :to="{ name : route.path }" :key="key">
          {{route.name}}
        </router-link>
      </li>
      <!--LOGGED USER-->
      <li v-if="$auth.check(1)" v-for="(route, key) in routes.user" v-bind:key="route.path">
        <router-link  :to="{ name : route.path }" :key="key">
          {{route.name}}
        </router-link>
      </li>
      <!--LOGGED ADMIN-->
      <li v-if="$auth.check(2)" v-for="(route, key) in routes.admin" v-bind:key="route.path">
        <router-link  :to="{ name : route.path }" :key="key">
          {{route.name}}
        </router-link>
      </li>
      <!--LOGOUT-->
      <li v-if="$auth.check()">
        <a href="#" @click.prevent="$auth.logout()">Logout</a>
      </li>
    </ul>
  </nav>
</template>

<script>
  export default {
    data() {
      return {
        routes: {
          // UNLOGGED
          unlogged: [
            {
              name: 'Inscription',
              path: 'register'
            },
            {
              name: 'Connexion',
              path: 'login'
            }
          ],

          // LOGGED USER
          user: [
            {
              name: 'Dashboard',
              path: 'dashboard'
            }
          ],
          // LOGGED ADMIN
          admin: [
            {
              name: 'Dashboard',
              path: 'admin.dashboard'
            }
          ]
        }
      }
    },
    mounted() {
      //
    }
  }
</script>