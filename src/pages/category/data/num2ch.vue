<template>
    <v-card title="数字大小写转换" max-width="500">
        <v-card-text>
            <v-textarea
                label="请输入"
                name="val"
                v-model="val"
            ></v-textarea>

            <v-btn color="success" class="mr-5" @click="tocn()">数字转中文</v-btn>
            <v-btn color="success" class="mr-5" @click="tonum()">中文转数字</v-btn>
            <v-btn color="warning" @click="clear()">清空</v-btn>
            <div id="result" class="p-2">
                <ul>
                    <li>中文小写：{{chResult.chLower}}</li>
                    <li>中文大写：{{chResult.chUpper}}</li> 
                    <li>数字：{{numResult}}</li>
                </ul>
            </div>
            </v-card-text>
    </v-card>
</template>
<script setup lang="ts">
import {ref} from 'vue'
import nzh from 'nzh/cn'
const val = ref()

const chResult = ref({
    "chLower": "",
    "chUpper": "",
})
const numResult = ref()

const clear = () => {
    val.value = ''
    chResult.value.chLower = ''
    chResult.value.chUpper = ''
    numResult.value = ''
}
const tocn = () => {
    // convert number string to chinese number
    let num : number ;
    if (val.value.search(".") > -1) {
        num = parseFloat(val.value)
    }else {
        num = parseInt(val.value)
    }
    chResult.value.chLower = nzh.encodeS(num)
    chResult.value.chUpper = nzh.encodeB(num)
    numResult.value = val.value
}

const tonum = () => {
    numResult.value = nzh.decodeS(val.value)
    if (numResult.value == 0) {
        numResult.value = nzh.decodeB(val.value)
    }
}
</script>