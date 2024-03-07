<script>
	import Header from "./components/Header.svelte";
	import Footer from "./components/Footer.svelte";
	import Tabs from "./shared/Tabs.svelte";
	import CreatePollForm from "./components/CreatePollForm.svelte";
	import PollList from "./components/PollList.svelte";
	//tabs
	let items = ['Current polls', 'Add new Poll'];
	let activeItem = 'Current polls'

	const tabChange = (e)=>{
		activeItem = e.detail;
	}
	let polls = [
		{
			id:1,
			question:'Python or JavaScript',
			answerA:'Python',
			answerB:'JavaScript',
			votesA:9,
			votesB:15
		},
	]
	const handleAdd = (e)=>{
		//e.preventDefault()
		const poll = e.detail;
		polls = [poll,...polls];
		console.log(polls);
		activeItem = 'Current polls';
	}
	const handleVotes = (e)=>{
		const { id, option} = e.detail;
		let copiedPolls = [...polls];
		let upVotedPoll = copiedPolls.find((poll)=> poll.id == id);

		if(option === 'a'){
			upVotedPoll.votesA++;
		}if(option === 'b'){
			upVotedPoll.votesB++;
		}
		polls = copiedPolls;
	}
</script>

<Header/>
<main>
	<Tabs items={items} activeItem={activeItem} on:tabChange={tabChange} />
	{#if activeItem === 'Current polls'}
	<p> <PollList  polls={polls} on:vote={handleVotes}/></p>
	{:else if activeItem === 'Add new Poll'}
	<p> <CreatePollForm on:add={handleAdd}/></p>
	{/if}
</main>
<Footer/>
<style>
	main{
		max-width:960px;
		margin:40px auto;

	}
	
</style>