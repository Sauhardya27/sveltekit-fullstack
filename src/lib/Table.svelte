<script>
    export let names
</script>

<div
	class="mt-10 pt-10 w-full max-w-2xl p-12 mx-auto rounded-lg shadow-xl dark:bg-white/10 bg-white/30 ring-1 ring-gray-900/5 backdrop-blur-lg"
>
	<div class="flex items-center justify-between mb-4">
		<div class="space-y-1">
			<h2 class="text-xl font-semibold">List of Users</h2>
			<p class="text-sm text-gray-500">
				Fetched {names.length} users
			</p>
		</div>
	</div>
	<div class="divide-y divide-gray-900/5">
		{#each names as user (user.id)}
			<div class="flex items-center justify-between py-3">
				<div class="flex items-center space-x-4">
					<div class="flex">
						<p class="font-medium pt-1 leading-none">{user.name}</p>
						<p class="font-medium pl-5 text-gray-500 pt-0">{user.email}</p>                        
					</div>
				</div>
                <form method="POST" action="/profiles?/delete">
                <input type="hidden" name="id" id="id" value={user.id}>
                <button type="submit" class="bg-red-500 px-2 py-2 rounded-lg">
                    <img class="w-4 float-right" src="./trash-can.svg" alt="delete"/>
                </button>
                </form>
			</div>
			<div class="flex items-center justify-between">
				<form method="POST" action="/profiles?/update">
					<input type="hidden" name="id" value={user.id}>
					<div class="flex items-center space-x-4">
						<div>
							<label for="name" class="font-semibold">Name:</label>
							<input type="text" id="name" name="name" required placeholder="Enter name to update" class="appearance-none bg-gray-200 border-gray-200 py-2 rounded-md pl-4 focus:bg-white focus:border-gray-500">
						</div>
						<div>
							<label for="email" class="font-semibold">Email:</label>
							<input type="email" id="email" name="email" required placeholder="Enter email to update" class="appearance-none bg-gray-200 border-gray-200 py-2 rounded-md pl-4 focus:bg-white focus:border-gray-500">
						</div>
						<button type="submit" class="font-semibold bg-green-400 rounded-lg px-6 py-2 text-white">Update</button>
					</div>
				</form>
			</div>
		{/each}
	</div>
</div>