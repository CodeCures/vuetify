<template>
    <v-container>
        <v-row class="mt-5">
            <v-col cols="4" offset="4">
                <v-card>
                    <v-card-title>Signup</v-card-title>
                    <v-card-text>
                        <v-form>
                            <v-text-field label="Usernam" type="text" />
                            <v-text-field label="Email" type="email" />
                            <v-autocomplete
                                v-model="value"
                                :items="browsers"
                                dense
                                filled
                                label="Which Browser do you Prefer"
                            ></v-autocomplete>
                            <v-file-input label="Attach a File" />
                            <v-dialog
                                ref="dialog"
                                v-model="modal"
                                :return-value.sync="date"
                                persistent
                                width="290px"
                            >
                                <template v-slot:activator="{ on, attrs }">
                                <v-text-field
                                    v-model="date"
                                    label="Picker in dialog"
                                    prepend-icon="mdi-calendar"
                                    readonly
                                    v-bind="attrs"
                                    v-on="on"
                                ></v-text-field>
                                </template>
                                <v-date-picker
                                v-model="date"
                                scrollable
                                >
                                <v-spacer></v-spacer>
                                <v-btn
                                    text
                                    color="primary"
                                    @click="modal = false"
                                >
                                    Cancel
                                </v-btn>
                                <v-btn
                                    text
                                    color="primary"
                                    @click="$refs.dialog.save(date)"
                                >
                                    OK
                                </v-btn>
                                </v-date-picker>
                            </v-dialog>
                            <v-divider></v-divider>
                            <v-card-actions>
                                <v-spacer></v-spacer>
                                <v-btn color="success" class="mt-2" >Register</v-btn>
                            </v-card-actions>
                        </v-form>
                    </v-card-text>
                </v-card>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
    export default {
        data() {
            return {
                browsers: ["Internet Explorer", "Google Chrome", "FireFox", "Edge", "Safari"],
                value: '',
                date: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
                menu: false,
                modal: false,
            }
        },
    }
    
</script>