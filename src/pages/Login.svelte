<script >
  import PocketBase from 'pocketbase';
const client = new PocketBase('http://localhost:8090');
let listlogin = []
async function getlitslogin(){
const result = await client.Users.listAuthMethods();
console.log(result)
listlogin = result.authProviders
}
let redirecturl = "http://localhost:5173/redirect"
getlitslogin()
 function handlelogin(l,index){
  localStorage.setItem('provider',JSON.stringify(l))
  window.location.href = l.authUrl + redirecturl
}
</script>
{#each listlogin as l,index}
  <button
  on:click={handlelogin(l,index)}
  >{l.name}</button>
{/each}