<script>
	let activeTab = 'standings';

	// Placeholder data
	let standingsData = [
		{ name: 'Australia', played: 5, won: 3, lost: 2, points: 9 },
		{ name: 'England', played: 5, won: 2, lost: 3, points: 6 },
		{ name: 'India', played: 5, won: 4, lost: 1, points: 12 },
		{ name: 'Bangladesh', played: 5, won: 4, lost: 1, points: 12 }
	];

	let upcomingMatches = [
		{ name: 'Match 1', date: '2023-09-25', location: 'Stadium 1' },
		{ name: 'Match 2', date: '2023-09-28', location: 'Stadium 2' },
		{ name: 'Match 1', date: '2023-09-25', location: 'Stadium 1' },
		{ name: 'Match 2', date: '2023-09-28', location: 'Stadium 2' },
		{ name: 'Match 1', date: '2023-09-25', location: 'Stadium 1' },
		{ name: 'Match 2', date: '2023-09-28', location: 'Stadium 2' }
	];

	let previousResults = [
		{ match: 'Match A', winner: 'Team A', score: '150/5 - 120/8' },
		{ match: 'Match B', winner: 'Team C', score: '180/3 - 160/7' },
		{ match: 'Match A', winner: 'Team A', score: '150/5 - 120/8' },
		{ match: 'Match B', winner: 'Team C', score: '180/3 - 160/7' },
		{ match: 'Match A', winner: 'Team A', score: '150/5 - 120/8' },
		{ match: 'Match B', winner: 'Team C', score: '180/3 - 160/7' }
	];

	let topPlayers = [
		{ name: 'Player 1', runs: 350, wickets: 8 },
		{ name: 'Player 2', runs: 280, wickets: 5 },
		{ name: 'Player 3', runs: 150, wickets: 8 },
		{ name: 'Player 4', runs: 180, wickets: 5 }
	];

	function switchTab(tab) {
		activeTab = tab;
	}
</script>

<div class="container mx-auto">
	<div class="mt-16">
		<h1 class="font-bold text-[36px]">Match Info</h1>
		<div id="match-info" class="flex flex-wrap space-x-4 mt-7">
			<button
				class="bg-transparent hover:bg-[#FF33B7] text-rose-700 font-semibold hover:text-white py-2 px-4 border border-[#FFB2E4] hover:border-transparent rounded btn mt-2"
				on:click={() => switchTab('standings')}
			>
				Standings
			</button>
			<button
				class="bg-transparent hover:bg-[#FF33B7] text-rose-700 font-semibold hover:text-white py-2 px-4 border border-[#FFB2E4] hover:border-transparent rounded btn mt-2 "
				on:click={() => switchTab('matches')}
			>
				Matches
			</button>
			<button
				class="bg-transparent hover:bg-[#FF33B7] text-rose-700 font-semibold hover:text-white py-2 px-4 border border-[#FFB2E4] hover:border-transparent rounded btn mt-2"
				on:click={() => switchTab('results')}
			>
				Results
			</button>
			<button
				class="bg-transparent hover:bg-[#FF33B7] text-rose-700 font-semibold hover:text-white py-2 px-4 border border-[#FFB2E4] hover:border-transparent rounded btn mt-2"
				on:click={() => switchTab('top-players')}
			>
				Top Players
			</button>
		</div>
	
		<div class="my-7">
			<div class="overflow-x-auto">
				{#if activeTab === 'standings'}
					<table class="min-w-full bg-white border rounded-lg shadow overflow-hidden">
						<thead class="bg-[#320073] border-b">
							<tr>
								<th class="border px-6 py-3 text-left font-semibold text-gray-200">Team</th>
								<th class="border px-6 py-3 text-left font-semibold text-gray-200">Played</th>
								<th class="border px-6 py-3 text-left font-semibold text-gray-200">Won</th>
								<th class="border px-6 py-3 text-left font-semibold text-gray-200">Lost</th>
								<th class="border px-6 py-3 text-left font-semibold text-gray-200">Points</th>
							</tr>
						</thead>
						<tbody>
							{#each standingsData as team}
								<tr>
									<td class="border-2 px-6 py-4 whitespace-nowrap">{team.name}</td>
									<td class="border-2 px-6 py-4 whitespace-nowrap">{team.played}</td>
									<td class="border-2 px-6 py-4 whitespace-nowrap">{team.won}</td>
									<td class="border-2 px-6 py-4 whitespace-nowrap">{team.lost}</td>
									<td class="border-2 px-6 py-4 whitespace-nowrap">{team.points}</td>
								</tr>
							{/each}
						</tbody>
					</table>
				{/if}
	
				{#if activeTab === 'matches'}
					<table class="min-w-full bg-white border rounded-lg shadow overflow-hidden">
						<thead class="bg-[#320073] border-b">
							<tr>
								<th class="border-2 px-6 py-3 text-left font-semibold text-gray-200">Match</th>
								<th class="border-2 px-6 py-3 text-left font-semibold text-gray-200">Date</th>
								<th class="border-2 px-6 py-3 text-left font-semibold text-gray-200">Location</th>
							</tr>
						</thead>
						<tbody>
							{#each upcomingMatches as match}
								<tr>
									<td class="border-2 px-6 py-4 whitespace-nowrap">{match.name}</td>
									<td class="border-2 px-6 py-4 whitespace-nowrap">{match.date}</td>
									<td class="border-2 px-6 py-4 whitespace-nowrap">{match.location}</td>
								</tr>
							{/each}
						</tbody>
					</table>
				{/if}
	
				{#if activeTab === 'results'}
					<table class="min-w-full bg-white border rounded-lg shadow overflow-hidden">
						<thead class="bg-[#320073] border-b">
							<tr>
								<th class="border-2 px-6 py-3 text-left font-semibold text-gray-200">Match</th>
								<th class="border-2 px-6 py-3 text-left font-semibold text-gray-200">Winner</th>
								<th class="border-2 px-6 py-3 text-left font-semibold text-gray-200">Score</th>
							</tr>
						</thead>
						<tbody>
							{#each previousResults as result}
								<tr>
									<td class="border-2 px-6 py-4 whitespace-nowrap">{result.match}</td>
									<td class="border-2 px-6 py-4 whitespace-nowrap">{result.winner}</td>
									<td class="border-2 px-6 py-4 whitespace-nowrap">{result.score}</td>
								</tr>
							{/each}
						</tbody>
					</table>
				{/if}
	
				{#if activeTab === 'top-players'}
					<table class="min-w-full bg-white border rounded-lg shadow overflow-hidden">
						<thead class="bg-[#320073] border-b">
							<tr>
								<th class="border-2 px-6 py-3 text-left font-semibold text-gray-200">Player</th>
								<th class="border-2 px-6 py-3 text-left font-semibold text-gray-200">Runs</th>
								<th class="border-2 px-6 py-3 text-left font-semibold text-gray-200">Wickets</th>
							</tr>
						</thead>
						<tbody>
							{#each topPlayers as player}
								<tr>
									<td class="border-2 px-6 py-4 whitespace-nowrap">{player.name}</td>
									<td class="border-2 px-6 py-4 whitespace-nowrap">{player.runs}</td>
									<td class="border-2 px-6 py-4 whitespace-nowrap">{player.wickets}</td>
								</tr>
							{/each}
						</tbody>
					</table>
				{/if}
			</div>
		</div>
	</div>
</div>

<hr />
