<template>
    <v-navigation-drawer
            v-model="drawer"
            :clipped="$vuetify.breakpoint.lgAndUp"
            app
    >
        <v-list dense>
            <template v-for="item in items">
                <v-layout
                        v-if="item.heading"
                        :key="item.heading"
                        align-center
                >
                    <v-flex xs6>
                        <v-subheader v-if="item.heading">
                            {{ item.heading }}
                        </v-subheader>
                    </v-flex>
                    <v-flex
                            xs6
                            class="text-center"
                    >
                        <a
                                href="#!"
                                class="body-2 black--text"
                        >EDIT</a>
                    </v-flex>
                </v-layout>
                <v-list-group
                        v-else-if="item.children"
                        :key="item.text"
                        v-model="item.model"
                        :prepend-icon="item.model ? item.icon : item['icon-alt']"
                        append-icon=""
                >
                    <template v-slot:activator>
                        <v-list-item>
                            <v-list-item-content>
                                <v-list-item-title>
                                    {{ item.text }}
                                </v-list-item-title>
                            </v-list-item-content>
                        </v-list-item>
                    </template>
                    <v-list-item
                            v-for="(child, i) in item.children"
                            :key="i"
                            @click=""
                    >
                        <v-list-item-action v-if="child.icon">
                            <v-icon>{{ child.icon }}</v-icon>
                        </v-list-item-action>
                        <v-list-item-content>
                            <v-list-item-title>
                                {{ child.text }}
                            </v-list-item-title>
                        </v-list-item-content>
                    </v-list-item>
                </v-list-group>
                <v-list-item
                        v-else
                        :key="item.text"
                        @click=""
                >
                    <v-list-item-action>
                        <v-icon>{{ item.icon }}</v-icon>
                    </v-list-item-action>
                    <v-list-item-content>
                        <v-list-item-title>
                            {{ item.text }}
                        </v-list-item-title>
                    </v-list-item-content>
                </v-list-item>
            </template>
        </v-list>

        <v-progress-linear
                color="blue-grey"
                height="25"
                reactive
        >
            <strong>{{ Math.ceil(33) }}%</strong>
        </v-progress-linear>
    </v-navigation-drawer>
</template>

<script>
    export default {
        data: () => ({
            drawer:null,
            items: [
                {
                    icon: 'folder',
                    'icon-alt': 'folder',
                    text: 'Files',
                    model: false,
                    children: [
                        {icon: 'folder', text: 'Folder 1'},
                        {icon: 'folder', text: 'Folder 2'},
                        {icon: 'folder', text: 'Folder 3'},
                        {icon: 'folder', text: 'Folder 4'},
                    ],
                },
                {icon: 'folder_special', text: 'Archives'},
                {icon: 'delete_forever', text: 'Trash'},
            ],
        }),
    }
</script>