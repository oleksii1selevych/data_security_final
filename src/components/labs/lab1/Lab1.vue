<template>
    <TheTaskWrapper :task-file-name="taskFileName" :report-file-name="reportFileName">
        <h1 class="text-center mb-5">Lab 1</h1>
        <base-collapsible title="DES Cryptography (encryption, decryption)">
            <des-cryptography />
        </base-collapsible>
    </TheTaskWrapper>
</template>


<script>
import TheTaskWrapper from '../../layout/TheTaskWrapper.vue';
import DesCryptography from './DesCryptography.vue';

export default {
     components:{ TheTaskWrapper, DesCryptography },
     data(){
        return {
            reportFileName:'lab1Task.pdf',
            taskFileName:'lab1Task.pdf'
        }        
     }
}

</script>

<style scoped>

h1 {
    color:#1c1d1f;
    font-weight: 200;
}

</style>