<template>
    <v-app id="inspire">
        <v-container
                grid-list-md
        >
            <h2 class="headline font-weight-regular">Recent Files</h2>
            <v-layout wrap d-flex mt-3>

                <v-flex v-for="i in 4" :key="`3${i}`" xs3 text-center>
                    <v-card white height="120px">
                        <v-card-text class="px-0">3</v-card-text>
                    </v-card>
                </v-flex>
            </v-layout>

            <h2 class="headline font-weight-regular mt-3 mb-4">All Files</h2>
            <v-data-table
                    v-model="selected"
                    :headers="headers"
                    :items="desserts"
                    item-key="name"
                    show-select
                    class="elevation-1"
                    fixed-header="true"

            >
                <template v-slot:top>
                    <span class="pa-3"></span>
                </template>
            </v-data-table>
        </v-container>


        <v-speed-dial
                bottom
                color="primary darken-1"
                dark
                fab
                fixed
                right
                :transition="true"
        >
            <template v-slot:activator>
                <v-btn
                        v-model="fab"
                        color="blue darken-2"
                        dark
                        fab
                >
                    <v-icon v-if="fab">close</v-icon>
                    <v-icon v-else>add</v-icon>
                </v-btn>
            </template>
            <v-btn
                    fab
                    dark
                    medium
                    color="green"
                    @click="dialog = !dialog"
            >
                <v-icon>create_new_folder</v-icon>
            </v-btn>
            <v-btn
                    fab
                    dark
                    medium
                    color="indigo"
                    @click="dialog2 = !dialog2"
            >
                <v-icon>file_copy</v-icon>
            </v-btn>
        </v-speed-dial>
        <v-dialog v-model="dialog" max-width="500px">
            <v-card>
                <v-card-text>
                    <v-text-field label="File name"></v-text-field>
                </v-card-text>
                <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn text color="primary" @click="dialog = false">Create Folder</v-btn>
                </v-card-actions>
            </v-card>
        </v-dialog>
        <v-dialog v-model="dialog2" persistent max-width="800px" max-height="560px">
            <v-card>
                <v-card-title class="headline">Upload Files</v-card-title>
                <v-card-text>Let Google help apps determine location. This means sending anonymous location data to
                    Google, even when no apps are running.
                </v-card-text>
                <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn color="green darken-1" text @click="dialog2 = false">Disagree</v-btn>
                    <v-btn color="green darken-1" text @click="dialog2 = false">Agree</v-btn>
                </v-card-actions>
            </v-card>
        </v-dialog>
    </v-app>
</template>

<script>
    export default {
        data() {
            return {
                dialog: false,
                dialog2: false,
                selected: [],
                headers: [
                    {
                        text: 'Dessert (100g serving)',
                        align: 'left',
                        sortable: false,
                        value: 'name',
                    },
                    { text: 'Calories', value: 'calories' },
                    { text: 'Fat (g)', value: 'fat' },
                    { text: 'Carbs (g)', value: 'carbs' },
                    { text: 'Protein (g)', value: 'protein' },
                    { text: 'Iron (%)', value: 'iron' },
                ],
                desserts: [
                    {
                        name: 'Frozen Yogurt',
                        calories: 159,
                        fat: 6.0,
                        carbs: 24,
                        protein: 4.0,
                        iron: '1%',
                    },
                    {
                        name: 'Ice cream sandwich',
                        calories: 237,
                        fat: 9.0,
                        carbs: 37,
                        protein: 4.3,
                        iron: '1%',
                    },
                    {
                        name: 'Eclair',
                        calories: 262,
                        fat: 16.0,
                        carbs: 23,
                        protein: 6.0,
                        iron: '7%',
                    },
                    {
                        name: 'Cupcake',
                        calories: 305,
                        fat: 3.7,
                        carbs: 67,
                        protein: 4.3,
                        iron: '8%',
                    },
                    {
                        name: 'Gingerbread',
                        calories: 356,
                        fat: 16.0,
                        carbs: 49,
                        protein: 3.9,
                        iron: '16%',
                    },
                    {
                        name: 'Jelly bean',
                        calories: 375,
                        fat: 0.0,
                        carbs: 94,
                        protein: 0.0,
                        iron: '0%',
                    },
                    {
                        name: 'Lollipop',
                        calories: 392,
                        fat: 0.2,
                        carbs: 98,
                        protein: 0,
                        iron: '2%',
                    },
                    {
                        name: 'Honeycomb',
                        calories: 408,
                        fat: 3.2,
                        carbs: 87,
                        protein: 6.5,
                        iron: '45%',
                    },
                    {
                        name: 'Donut',
                        calories: 452,
                        fat: 25.0,
                        carbs: 51,
                        protein: 4.9,
                        iron: '22%',
                    },
                    {
                        name: 'KitKat',
                        calories: 518,
                        fat: 26.0,
                        carbs: 65,
                        protein: 7,
                        iron: '6%',
                    },
                ],
            }
        },
        props: {
            source: String,
        }
    }
</script>
