<template>
    <v-alert v-model="exibir" dismissible :color="tipo" transition="scale-transition" outline class="pa-1" >
        <ul class="pl-3">
            <li v-for="(msg, key) in value" :key="key"> 
                {{msg}} 

                <v-tooltip v-if="key==0 && tooltip" bottom>
                    <template v-slot:activator="{ on }">
                        <v-icon color="primary" dark v-on="on" style="cursor:pointer; font-size:21px">help</v-icon>
                    </template>
                    <span> {{tooltip}} </span>
                </v-tooltip>
            </li>
        </ul>
    </v-alert>
</template>

<script>
    export default {
        props: {
            value:Array, tipo:String,
            tooltip:String,
        },
        data: function () {
            return {
                exibir: this.value ? Object.keys(this.value).length > 0 : false
            }
        },
        watch:{
            value(v){
                this.exibir = v ? Object.keys(v).length : false
            },
        },
    }
 </script>