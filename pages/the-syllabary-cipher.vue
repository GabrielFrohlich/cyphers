<template>
    <NuxtLayout>
        <template #content>
            <div class="container mx-auto">
                <table class="text-white border-spacing-0.5">
                    <tr v-for="(item, index) in arrLines">
                        <td v-for="arr2 in item" class="p-2">
                            {{ index.toString() }}{{ arr2.toString() }}<br>
                            <input type="text" :name="`${index}${arr2}`" class="text-black w-12" v-model="values[`${index}${arr2}`]">
                        </td>
                    </tr>
                </table>
            </div>
            <div class="container mx-auto">
                <textarea name="toDecrypt" id="" v-model="rawText">
                </textarea>
                <button @click="decrypt()">Decrypt</button><br>
                <span class="text-white">{{decrypted}}</span>
            </div>
        </template>
    </NuxtLayout>
</template>

<script setup lang="ts">
const arrLines:Array<any> = []
for (let i = 0; i < 10; i++) {
    const arrColumns = []
    for (let x = 0; x < 10; x++) {
        arrColumns.push(x)
    }

    arrLines.push(arrColumns)
}

const values:any = {}
let rawText ="";
let decrypted = '';
let decryptedArr = [];

function decrypt(){
    let lastChar = 0;
    for(let k = 0; k<rawText.length/2; k++){
        console.log(rawText.substring(lastChar, lastChar+2))
        decrypted += values[rawText.substring(lastChar, lastChar+2)]
        decryptedArr.push(values[rawText.substring(lastChar, lastChar+2)])
        lastChar += 2;
    }
}

</script>