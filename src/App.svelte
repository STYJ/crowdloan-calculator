
<script>
	let ticker = "SDN";
	let ploTokenAllocation = 15400000;
	let ksmCollected = 500000;
	let price = 5;
	let totalSupply = 70000000;
	let ksmPrice = 450;

	var formatter = new Intl.NumberFormat('en-US', {
  		style: 'currency',
  		currency: 'USD',
	});
</script>


<main>
	<h1>Crowdloan Calculator <span class="sub">Made by <a href="https://twitter.com/itsmeSTYJ">Simon</a></span></h1>
	
	<p>Estimate your returns from participating in the Kusama parachain auction!</p>

	<h3>0. Input token details</h3>
	<div>
		<label for="ticker">Token Symbol:</label>
  		<input type="text" id="ticker" bind:value={ticker}>
	</div>
	<div>
		<label for="totalSupply">Total Supply:</label>
  		<input type="text" id="totalSupply" bind:value={totalSupply}>
	</div>
	
	<h3>1. Input crowdloan variables</h3>
	
	<div>
		<label for="ploTokenAllocation">Total {ticker} offered for crowdloan:</label>
  		<input type="text" id="ploTokenAllocation" bind:value={ploTokenAllocation}>
	</div>
	<div>
		<label for="ksmCollected">Total KSM contributed:</label>
  		<input type="text" id="ksmCollected" bind:value={ksmCollected}>
	</div>
	<div>
		<label for="rate">Current {ticker}/KSM rate:</label>
		<span id="rate">{+(ploTokenAllocation / ksmCollected).toFixed(2)}</span>
	</div>

	<h3>2. Input estimated price of {ticker}</h3>
	<div>
		<label for="price">Price:</label>
		<div style="display: inline-block; width: 200px;">
			<input type="text" id="price" bind:value={price}>		
		</div>
	</div>
	<div>
		<label for="marketCap">Estimated market cap:</label>
		<span id="marketCap"> {formatter.format(price * totalSupply)}</span>
	</div>
	<h3>3. Input current price of KSM to estimate returns</h3>
	<div>
		<label for="ksmPrice">Current KSM price:</label>
  		<input type="text" id="ksmPrice" bind:value={ksmPrice}>
	</div>
	<div>
		<label for="estimatedReturns">Estimated returns:</label>
		<span id="estimatedReturns" style="font-size: larger; font-weight: 700; color: #ff3e00;">{+(ploTokenAllocation / ksmCollected * price * 100/ksmPrice).toFixed(2)}%</span>
	</div>
	<span class="sub" style="">Formula = rate * token price * 100 / ksm price. The rate used assumes no bonuses.</span>
	<h3>4. Decide if crowdloan returns + X months lock is better than staking KSM for 12% returns + 1 week lock</h3>
</main>

<style>
	main {
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
	}

	label {
		display: contents;
	}

	.sub {
		color: grey;
		font-size: x-small;
	}

	@media (min-width: 480px) {
		main {
			max-width: none;
		}
	}
</style>