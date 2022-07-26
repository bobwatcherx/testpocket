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

// async function handlelogin(l,index){
// const authData = await client.Users.authViaOAuth2(
//     l.name, 
//   "CODE",
//    "VERIFIER",
//     "REDIRECT_URL"
//     ).then((authdata)=>{
//       console.log(authdata)
//     }).catch(err=>console.log(err))
// }
</script>
{#each listlogin as l,index}
  <button
  on:click={handlelogin(l,index)}
  >{l.name}</button>
{/each}