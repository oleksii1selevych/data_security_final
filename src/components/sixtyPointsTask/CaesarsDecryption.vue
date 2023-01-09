<template>
    <div class="row mb-3">
        <div class="col">
            <label for="decryptionFile" class="form-label">Файл для декодування:</label>
            <input class="form-control" type="file" ref="file" @change="readFile" id="decryptionFile" />
        </div>
        <div class="col">
            <label class="form-label" for="shift">Ключ:</label>
            <input type="number" id="shift" v-model.number="shift" class="form-control" :placeholder="0" />
        </div>
        <div class="col">
            <label class="form-label" for="language">Мова:</label>
            <select class="form-select" v-model.trim="language" id="language">
                <option selected value="Ru">Російська</option>
                <option value="En">Англійська</option>
            </select>
        </div>
    </div>
    <div class="d-flex justify-content-center">
        <base-button @click="decipherFile" mode="flat">Дешифрувати</base-button>
    </div>
</template>

<script>

import { decrypt } from '../../helpers/caesarsCipher.js';

export default {
    data() {
        return {
            decryptionFile: null,
            shift: 0,
            language: "Ru"
        }
    },
    methods: {
        readFile() {
            this.decryptionFile = this.$refs.file.files[0];
        },
        decipherFile() {

            const reader = new FileReader();
            
            reader.readAsText(this.decryptionFile);
            reader.onload = () => {
                const inputFile = decrypt(this.shift, reader.result, this.language);
                const link = document.createElement("a");
                link.download = "inputMessageFile.txt";

                let blobData = new Blob([inputFile], {
                    type: "text/plain"
                });
                link.href = window.URL.createObjectURL(blobData);
                link.click();
            };
        }
    }
}

</script>



