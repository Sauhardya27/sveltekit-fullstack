<script lang="ts">
	import { PrivateKey } from "@bsv/sdk";

	let WIF:string
	let address:string

	function createKeys () {
		const privKey = PrivateKey.fromRandom()
		WIF = privKey.toWif()
		console.log("Private Key WIF format is ", WIF)
		address = privKey.toAddress()
		console.log("Your bitcoin address is ", address)
	}

</script>

<section>
	<button on:click={createKeys} class="bg-black text-white p-2 rounded-lg mx-auto"> Generate New Wallet Keys </button>
	<p>Private Key WIF format is {WIF}</p>
	<p>Your Bitcoin Address is {address}</p>
</section>
