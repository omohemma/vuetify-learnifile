<template>
    <v-app-bar
            :clipped-left="$vuetify.breakpoint.lgAndUp"
            app
            color="primary darken-1"
            dark
    >
        <v-toolbar-title
                style="width: 300px"
                class="ml-0 pl-4"
        >
            <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
            <span class="hidden-sm-and-down">File Manager</span>
        </v-toolbar-title>
        <v-text-field
                flat
                solo-inverted
                hide-details
                prepend-inner-icon="search"
                label="Search"
                class="hidden-sm-and-down"
        ></v-text-field>
        <v-spacer></v-spacer>
        <v-btn
                icon
                large
        >
            <v-avatar>
                <img
                        src="https://cdn.vuetifyjs.com/images/john.jpg"
                        alt="John"
                >
            </v-avatar>

        </v-btn>
        <span class="hidden-sm-and-down" >{{name}}</span>
    </v-app-bar>
</template>

<script>
    export default {
        data() {
            return{
                name:'Tim GodFrey'
            }

        }

    }
</script>