<template>
    <v-card title="进制转换" max-width="400">
        <v-card-text>
            <v-defaults-provider :defaults="{'VTextField': {'variant': 'outlined'}}">
            <v-text-field
                name="binary"
                label="二进制"
                v-model="binary"
            ></v-text-field>
            <v-text-field
                name="octal"
                label="八进制"
                v-model="octal"
            ></v-text-field>
            <v-text-field
                name="decimal"
                label="十进制"
                v-model="decimal">
            </v-text-field>
            <v-text-field
                name="hexadecimal"
                label="十六进制"
                v-model="hexadecimal">
                </v-text-field>
            </v-defaults-provider>
        </v-card-text>
    </v-card>
    </template>
    <script setup lang="ts">
    import {ref, watch} from 'vue'

    const binary=ref()
    const octal=ref()
    const decimal=ref()
    const hexadecimal=ref()

    // const num = ref({
    //     binary: '0101',
    //     octal: '',
    //     decimal: '',
    //     hexadecimal: ''
    // })

    watch(decimal, async(newNum, oldNum) => {
        convert(newNum, "10");
    })

    watch(binary, async(newNum, oldNum) => {
        convert(newNum, "2");
    })

    watch(octal, async(newNum, oldNum) => {
        convert(newNum, "8");
    })

    watch(hexadecimal, async(newNum, oldNum) => {
        convert(newNum, "16");
    })

    const convert = (v: string, unit: string) => {
        if (v == "") {
            // reset all num to ""
            binary.value = "";
            octal.value = "";
            decimal.value = "";
            hexadecimal.value = "";
            return;
        }

        let curDecimal = 0;
        if (unit == "2") {
            binary.value = v;
            curDecimal = parseInt(v, 2);
        } else if (unit == "8") {
            octal.value = v;
            curDecimal = parseInt(v, 8);
        } else if (unit == "10") {
            decimal.value = v;
            curDecimal = parseInt(v, 10);
        } else if (unit == "16") {
            hexadecimal.value = v;
            curDecimal = parseInt(v, 16);
        }
        // convert to other units
        binary.value = curDecimal.toString(2);
        octal.value = curDecimal.toString(8);
        decimal.value = curDecimal.toString(10);
        hexadecimal.value = curDecimal.toString(16);
    }
    </script>