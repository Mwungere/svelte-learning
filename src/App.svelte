<script>
	import CreatePollFrom from "./components/CreatePollForm.svelte";
  import Footer from "./components/Footer.svelte";
	import Header from "./components/Header.svelte"; 
	import PollList from "./components/PollList.svelte";
	import Tabs from "./shared/Tabs.svelte";
  
	//tabs
	let items = ['Current Polls', 'Add New Poll'];
	let activeItem = 'Current Polls';
	const tabChange = (e) => {
	  activeItem = e.detail;
	}
  
	// polls
	let polls = [
	  {
		id: 1,
		question: 'Python or JavaScript?',
		answerA: 'Python',
		answerB: 'JavaScript',
		votesA: 9,
		votesB: 15,
	  },
	];
  
	const handleAdd = (e) => {
	  let poll = e.detail;
	  polls = [poll, ...polls];
	  console.log(polls);
	  activeItem='Current Polls';
	}
  
	const handleVote = (e) => {
	  const {id, option} = e.detail;
	  let copiedPolls = [...polls];
	  let upvotedPoll = copiedPolls.find((poll) => poll.id == id);
  
	  if(option ==='a'){
		  upvotedPoll.votesA++;
	  }
	  if(option ==='b'){
		  upvotedPoll.votesB++;
	  }
	  polls=copiedPolls;
	}
  
  
  </script>
  
  <Header />
  
  <main>
	  <Tabs {items} {activeItem} on:tabChange = {tabChange} />
  
	  {#if activeItem === 'Current Polls'}
		  <PollList {polls} on:vote={handleVote} />
	  {:else if activeItem === 'Add New Poll'}
		  <CreatePollFrom on:add={handleAdd} />
	  {/if}
  </main>
  
  <Footer/>
  
  <style>
	  main{
		  max-width: 960px;
		  margin: 40px auto;
	  }
  </style>