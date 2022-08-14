<template>
 Paste Text: <br>
    <textarea name="output" cols="50" rows="12" v-model="rawText" placeholder="paste here"></textarea>
    <br>

<button type="button" @click="extractEmails">Get emails</button><br>
    <span class="counter"></span><br>
    Emails in text:<br>
    <textarea name="output" cols="50" rows="12" v-model="emails"></textarea>
    <div id="counter">Emails found: {{counter}}</div>
</template>

<script>  
export default {

      data(){
        return {
            rawText: '',
            emails:'',
            counter:0,
            emailData:[],
            exp : /([A-Za-z0-9._-]+@[a-zA-Z0-9._-]+\.[a-zA-Z0-9._-]+)/gi,
     
            }   
        },


    methods:{
        
        extractEmails(){
            this.emails = this.rawText.match(/([A-Za-z0-9._-]+@[a-zA-Z0-9._-]+\.[a-zA-Z0-9._-]+)/gi);
            this.emails = [...new Set(this.emails)],
            this.counter = this.emails.length; 
            
        },

        
    }
    
}
</script>

<style>

</style>