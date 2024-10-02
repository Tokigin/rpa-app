<script lang="ts">
	import { Dummy } from './Dummy';
	let first: string = '';
	let last: string = '';
	let company: string = '';
	let email: string = '';
	let phone: string = '';
	let role: string = '';
	let address: string = '';
	let table: any = [];

	const Add = () => {
		table.push({
			first: first,
			last: last,
			company: company,
			email: email,
			phone: phone,
			role: role,
			address: address
		});
		table = table;
		Clear();
	};
	const Clear = () => {
		first = '';
		last = '';
		company = '';
		email = '';
		phone = '';
		role = '';
		address = '';
	};
	const ClearTable = () => {
		table = [];
	};
	const AddDummy = () => {
		table = Dummy();
	};
</script>

<div class="container h-full mx-auto flex justify-center items-center gap-5">
	<div>
		<div class="grid grid-cols-2 gap-5">
			<label class="label">
				<span>First Name</span>
				<input
					bind:value={first}
					class="input variant-form-material"
					type="text"
					placeholder="Enter First Name here"
					name="First Name"
				/>
			</label>
			<label class="label">
				<span>Last Name</span>
				<input
					bind:value={last}
					class="input variant-form-material"
					type="text"
					placeholder="Enter Last Name here"
					name="last Name"
				/>
			</label>
			<label class="label">
				<span>Company Name</span>
				<input
					bind:value={company}
					class="input variant-form-material"
					type="text"
					placeholder="Enter Company Name here"
					name="Company Name"
				/>
			</label>
			<label class="label">
				<span>Email</span>
				<input
					bind:value={email}
					class="input variant-form-material"
					type="text"
					placeholder="Enter Email here"
					name="Email"
				/>
			</label>
			<label class="label">
				<span>Phone Number</span>
				<input
					bind:value={phone}
					class="input variant-form-material"
					type="text"
					placeholder="Enter Phone Number here"
					name="Phone Number"
				/>
			</label>
			<label class="label">
				<span>Role</span>
				<input
					bind:value={role}
					class="input variant-form-material"
					type="text"
					placeholder="Enter Role here"
					name="Role"
				/>
			</label>
			<label class="label">
				<span>Address</span>
				<input
					bind:value={address}
					class="input variant-form-material"
					type="text"
					placeholder="Enter Address here"
					name="lAddress"
				/>
			</label>
		</div>
		<div class="grid grid-cols-2 gap-5 pt-5">
			<button
				type="button"
				class=" bg-white/10 py-3 px-6 rounded-md hover:bg-black/50"
				on:click={Add}>Add Data</button
			>
			<button
				type="button"
				class=" bg-white/10 py-3 px-6 rounded-md hover:bg-black/50"
				on:click={Clear}>Clear Data</button
			>
			<button
				type="button"
				class=" bg-white/10 py-3 px-6 rounded-md hover:bg-black/50"
				on:click={AddDummy}>Add Dummy Data</button
			>
			<button
				type="button"
				class=" bg-white/10 py-3 px-6 rounded-md hover:bg-black/50"
				on:click={ClearTable}>Clear Table</button
			>
		</div>
	</div>

	<div class="h-[600px] table-container">
		<!-- Native Table Element -->
		<table class="table table-hover">
			<thead>
				<tr>
					<th>First Name</th>
					<th>Last Name</th>
					<th>Company Name</th>
					<th>Email</th>
					<th>Phone Number</th>
					<th>Role</th>
					<th>Address</th>
				</tr>
			</thead>
			<tbody>
				{#each table as row, i}
					<tr>
						<td>{row.first}</td>
						<td>{row.last}</td>
						<td>{row.company}</td>
						<td>{row.email}</td>
						<td>{row.phone}</td>
						<td>{row.role}</td>
						<td>{row.address}</td>
					</tr>
				{/each}
			</tbody>
		</table>
	</div>
</div>

<style lang="postcss">
	figure {
		@apply flex relative flex-col;
	}
	figure svg,
	.img-bg {
		@apply w-64 h-64 md:w-80 md:h-80;
	}
	.img-bg {
		@apply absolute z-[-1] rounded-full blur-[50px] transition-all;
		animation:
			pulse 5s cubic-bezier(0, 0, 0, 0.5) infinite,
			glow 5s linear infinite;
	}
	@keyframes glow {
		0% {
			@apply bg-primary-400/50;
		}
		33% {
			@apply bg-secondary-400/50;
		}
		66% {
			@apply bg-tertiary-400/50;
		}
		100% {
			@apply bg-primary-400/50;
		}
	}
	@keyframes pulse {
		50% {
			transform: scale(1.5);
		}
	}
</style>
