<template>
<div>
   
<nav>
    <v-app-bar flat >
        <!-- <v-app-bar-nav-icon
        @click="drawer=!drawer"
        fab
        depressed
        color="white">
            
            <v-icon color="grey">
                mdi-menu
            </v-icon>
        </v-app-bar-nav-icon> -->
        <v-app-bar-nav-icon>
            <v-img
            height="75px"
            contain
            src="@/assets/NavbarLogo.png"
            disable
            ></v-img>
        </v-app-bar-nav-icon>
        
        <v-toolbar-title class="text-uppercase grey--text">
            <span class="font-weight-light">awesome</span>
            <span class="font-weight-bold">wines</span>
        </v-toolbar-title>

        <v-spacer></v-spacer>
        
        <v-btn 
        temporary
        depressed
        color="white"
        v-for="button in buttons" :key="button.text" router :to="button.route">
            <span class="grey--text hidden-sm-and-down"> {{button.text}} </span>
            <v-icon color="grey" right>
                {{button.icon}}
            </v-icon>
        </v-btn>



    </v-app-bar>

    <v-navigation-drawer v-model="drawer" app temporary class="indigo lighten-4">
        <v-list>
            <v-list-item v-for="link in links" :key="link.text" router :to="link.route">
              <v-list-item-action>
                  <v-icon>
                    {{link.icon}}                 
                    </v-icon>
              </v-list-item-action> 
              <v-list-item-content>
              <v-list-item-title class="">
                {{link.text}}
              </v-list-item-title>
              </v-list-item-content>

            </v-list-item>
        </v-list>

    </v-navigation-drawer>

</nav>

    
</div>

</template>

<script>
export default{
     name: "nav-bar",
    data() {
        return {
            drawer: false,
            buttons: [
                 { icon: 'mdi-home', text: 'Home', route: '/' },
                 { icon: 'mdi-shopping', text: 'Store', route: '/store' },
                //  { icon: 'mdi-cart', text: 'cart', route: '/cart' },
                //  { icon: 'mdi-exit-to-app', text: 'Sign out', route: '/exit' },
            ],
            // links: [
            //      { icon: 'mdi-view-dashboard', text: 'Dashboard', route: '/' },
            //      { icon: 'mdi-folder', text: 'My Projects', route: '/projects' },
            //      { icon: 'mdi-account', text: 'Team', route: '/team' },
            // ]
        }
    },
    methods: {
        
        }
    }
   

</script>