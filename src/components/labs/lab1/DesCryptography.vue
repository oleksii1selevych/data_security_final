<template>
    <div class="row mb-3">
        <div class="col-sm-12 col-lg-6">
            <label for="key" class="form-label">Key:</label>
            <input class="form-control" v-model.trim="key" type="text" id="key" />
        </div>
    </div>
    <div class="row mb-3">
        <div class="col-lg-6 col-sm-12 mb-sm-3 mb-md-1">
            <label class="form-label" for="plainText">Plaintext</label>
            <textarea class="form-control" v-model.trim="plainText" id="plainText" type="text" rows="8"></textarea>
        </div>
        <div class="col-lg-6 col-sm-12 mb-md-1">
            <label class="form-label" for="plainText">Ciphertext</label>
            <textarea class="form-control" v-model.trim="cipherText" id="plainText" type="text" rows="8"></textarea>
        </div>
    </div>
    <div class="d-flex justify-content-center mt-2">
        <button @click="encryptPlainText" class="encrypt-btn">Encrypt</button>
        <button @click="decryptCipher" class="decrypt-btn">Decrypt</button>
    </div>
</template>


<script>

import { encrypt } from '../../../helpers/desAlgorithm.js';

export default {
    data(){
        return{
            plainText:'',
            cipherText:'',
            key:''
        }
    },
    methods:{
        encryptPlainText(){
            console.log(encrypt(this.plainText, this.key));            
        },
        decryptCipherText(){

        }
    }
}

</script>

<style scoped>

 button {
    outline: none;
    padding: 1rem 3rem;
    border: 1px solid transparent;
    background: none;
    color: white;
    font-weight: 700;
 }

 .encrypt-btn {
    background-color: #b9ceeb;
    border-radius:5px 0px 0px 5px;
 }

.encrypt-btn:hover{
    background-color:  #87a8d0;
}

 .decrypt-btn {
    background-color: #c3b4d2;
    border-radius:0px 5px 5px 0px;
 }

.decrypt-btn:hover{
    background-color:  #574b9b;
}

</style>