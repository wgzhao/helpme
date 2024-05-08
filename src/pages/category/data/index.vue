<template>
<v-row>
    <v-col cols="12" md="4">
        <v-card 
         max-width="200" 
         >
         <v-card-title>
         <router-link to="/category/data/hexconversion">
            进制转换
            </router-link>
            </v-card-title>
        </v-card>
    </v-col>
    <v-col cols="12" md="4">
        <v-card 
         max-width="200" 
         >
         <v-card-title>
         <router-link to="/category/data/num2ch">
            数字大小写转换
            </router-link>
            </v-card-title>
        </v-card>
    </v-col>
</v-row>
</template>
<script setup lang="ts">
import router from '../../../router';

</script>