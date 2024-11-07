<script lang="ts">
	let amount = '';
	let liquid = 0;
	let powder = 0;
	let language: 'pt' | 'en' = 'pt';
	const texts = {
		pt: {
			title: 'Calculadora de Jesmonite',
			totalAmount: 'Quantidade total em gramas',
			liquid: 'Líquido',
			powder: 'Pó'
		},
		en: {
			title: 'Jesmonite Calculator',
			totalAmount: 'Total amount in grams',
			liquid: 'Liquid',
			powder: 'Powder'
		}
	};

	$: {
		liquid = Math.round(Number(amount) / 3.5);
		powder = Math.round(Number(amount) - liquid);
	}
</script>

<div class="flex h-screen flex-col items-center md:justify-center">
	<div class="rounded-lg border border-gray-200 bg-gray-200 p-8 shadow-lg">
		<h1 class="text-center text-4xl font-bold">{texts[language].title}</h1>

		<div class="mt-4 flex items-center justify-center gap-2">
			<button
				class="rounded-md border border-gray-200 bg-white p-2"
				class:!bg-blue-500={language === 'pt'}
				class:text-white={language === 'pt'}
				on:click={() => (language = 'pt')}
			>
				Português
			</button>
			<button
				class="rounded-md border border-gray-200 bg-white p-2"
				class:!bg-blue-500={language === 'en'}
				class:text-white={language === 'en'}
				on:click={() => (language = 'en')}
			>
				English
			</button>
		</div>

		<div class="mt-8 flex flex-col items-center justify-center gap-2">
			<label for="amount" class="text-lg font-bold">{texts[language].totalAmount}</label>
			<input type="number" id="amount" class="p-2 text-center text-2xl" bind:value={amount} />
		</div>

		<div class="flex w-full items-center justify-around gap-4">
			<div class="mt-8 flex flex-col items-center justify-center gap-2">
				<span class="text-lg font-bold">{texts[language].liquid}</span>
				<span class="text-2xl">{liquid}g</span>
			</div>

			<div class="mt-8 flex flex-col items-center justify-center gap-2">
				<span class="text-lg font-bold">{texts[language].powder}</span>
				<span class="text-2xl">{powder}g</span>
			</div>
		</div>
	</div>
</div>
