<main id="app">
	{#if currIndex === 0}
		
		<Card  data={data[0]} on:arrow-clicked={changeView}/>
	{:else if currIndex === 1}
		<Card data={data[1]} on:arrow-clicked={changeView}/>
	{/if}
</main>
<svelte:window on:keyup={keyPress} />

<script>
	import Card from "./components/Card.svelte"
	let data = [
		{
			text:  "“ I’ve been interested in coding for a while but never taken the jump, until now. I couldn’t recommend this course enough. I’m now in the job of my dreams and so excited about the future. ”",
			name: "Tanya Sinclair",
			jop: "UX Engineer",
		},
		{
			text:  "“ If you want to lay the best foundation possible I’d recommend taking this course. The depth the instructors go into is incredible. I now feel so confident about starting up as a professional developer. ”",
			name: "John Tarkpor",
			jop: "Junior Front-end Developer",
		}
	]
	let currIndex = 0
	const changeView = ({detail}) => {
		currIndex += detail
		if(currIndex > data.length - 1 ) {
			currIndex = 0
		} else if ( currIndex < 0 ) {
			currIndex = data.length - 1
		}
	}
	const keyPress = (e) => {
		if(e.key === "ArrowRight") {
			changeView({detail:-1})
		} else if (e.key === "ArrowLeft") {
			changeView({detail:1})
		}
	}
</script>

<style type="text/scss">
    @import "./shared";
	#app {
		display: flex;
		align-items: center;
		justify-content: center;
		position: relative;
		img {
			display: flex;
			&.pattern-bg {
				position: absolute;
				z-index: -2;
	
			}
		}
	}
	:global(html) {
		min-width: 320px;
	}

</style>