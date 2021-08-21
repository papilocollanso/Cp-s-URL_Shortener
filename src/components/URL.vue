<template>
    <div class="container">

<div class="outside">

<form>
<fieldset>

  <legend><ul>
  <li class="text-success">Always use a valid URL</li>

</ul></legend>
  <div class="mb-3">
    <label for="URL" class="form-label">URL</label>
    <input type="url"   required v-model="url" class="form-control" id="shorUrlInput" aria-describedby="urlHelp">
 </div><br>

  <div class="mb-3">
    <label for="Result" class="form-label">Result</label>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span><i v-clipboard="results" @success="handleSuccess" @error="handleError" data-bs-toggle="tooltip"  data-bs-placement="top" title="Copy to clipboard"  class="fas fa-copy btn-clipboard "></i></span>
    <input type="url" v-bind:value="results" readonly  class="form-control" id="resultInput">
  </div><br>


  <div>
  <button type="submit" v-on:click.prevent="getUrl()" class="btn btn-primary mr-4">Shorten</button>
  <button type="submit"  v-on:click.prevent="expandUrl()"  class="btn btn-success">Expand</button>
  </div>         
    </fieldset> 
</form>
 
    </div>
        
  

    


    </div>
</template>

<script>
import 'dotenv';

// eslint-disable-next-line no-unused-vars
import { clipboard } from 'vue-clipboards';

    export default {
        name: "URL",
        data() {
          return {
            url:"",
            results:"",
            
          }
          
        },
        methods: {

         handleSuccess(){

           if(`${this.results}` != ""){
     
           alert("URL copied");
           }
          

          },
                   handleError(){
              alert("An error occured");
            

          },
        
          expandUrl(){
const url = new URL("https://t.ly/api/v1/link/expand");

let headers = {
    "Content-Type": "application/json",
    "Accept": "application/json",
}

let body = {
      // eslint-disable-next-line no-useless-escape
    "short_url": `https://${this.url}`,
    "password": "12Nkasiobi",
    "api_token": "process.env.VUE_APP_URL_API_KEY"
}

fetch(url, {
    method: "POST",
    headers: headers,
    body: JSON.stringify(body)
})
    .then(response => response.json())
    .then(json => this.results=json.long_url);
          },
          getUrl() {
           
            
const url = new URL("https://t.ly/api/v1/link/shorten");

let headers = {
    "Content-Type": "application/json",
    "Accept": "application/json",
}

let body = {
    // eslint-disable-next-line no-useless-escape
    "long_url": `http:\/\/${this.url}\/`,
    // eslint-disable-next-line no-useless-escape
    "domain": "https:\/\/t.ly\/",
    "api_token": "iqZANaJ5bDVwLCZFG3A9aF88PTnqHHAwuak2gvP6VT3bmS1sR6yBh1PqHal8"
}

fetch(url, {
    method: "POST",
    headers: headers,
    body: JSON.stringify(body)
})
    .then(response => response.json())
    .then(json => this.results=json.short_url);
          
          
          }
        },
    }
    
</script>

<style lang="scss" scoped>
.fa-copy:hover{
  color: green;
}
.outside{
margin: 30px;
border:solid #ccc 1px;
padding: 35px;
border-radius: 5px 5px 5px 5px;

}
li{
  font-size: 15px;
  list-style-type: circle;
  font-weight: bold;
  
}

</style>