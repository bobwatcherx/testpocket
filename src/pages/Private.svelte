<script >
	 import PocketBase from 'pocketbase';
const client = new PocketBase('http://localhost:8090');
		let getstorage = localStorage.getItem('provider')
let cekprovider = JSON.parse(getstorage)
   const params = (new URL(window.location)).searchParams;
let redirecturl = "http://localhost:5173/redirect"
if(!getstorage ){
	window.location.href = "/"
}
if(cekprovider.state !== params.get('state')){
		window.location.href = "/"
}
  function facebooklogin(){
	if(cekprovider.length !== 0 ){
		setTimeout(async()=>{
const authData = await client.Users.authViaOAuth2(
		cekprovider.name,
	   params.get("code"),
	  cekprovider.codeVerifier,
	   redirecturl
	   )
		.then((data)=>console.log(data))
		.catch(err=>console.log(err))
	console.log(cekprovider)
		},3000)
	}
}
facebooklogin()
</script>
private aja