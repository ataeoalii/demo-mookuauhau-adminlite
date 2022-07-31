<script lang="ts">
	import { isSignedIn, user } from '$lib/nhost';

	let step = 'welcome';
	let message = ''; // warning messages

	function signIn() {
		console.log("Signing in...");
		step = "add_person";
	}

	function addPerson() {
		console.log("Adding person...");
		step = "step_one";
	}

	function stepOne() {
		console.log("Step one...");
		step = "step_two";
	}

	function stepTwo() {
		step = "step_three";
	}

	function stepThree() {
		step = "add_person";
	}

</script>

<h2>Supporting Documentation Update</h2>

<div>
	Upload supporting documentation for a person and store it in a database for retrieval.
</div>

<div style="color:red">{step}</div>

{#if step === 'welcome'}

	<div id="welcome">
		<h3>E Komo Mai</h3>
		<input type="text" id="username" />
		<label for="username" class="mdc-floating-label">Username</label>
		<input type="password" id="password" />
		<label for="password" class="mdc-floating-label">Password</label>
		<div class="mdc-touch-target-wrapper">
			<button class="mdc-button mdc-button--raised" on:click={signIn}>
				<span class="mdc-button__ripple"></span>
				<span class="mdc-button__touch"></span>
				<span class="mdc-button__focus-ring"></span>
				<span class="mdc-button__label">Login</span>
			</button>
		</div>
	</div>
{:else if step === 'add_person'}
	<div id="add_person">
		<h3>Hello, [{user.name}]</h3>
		<div class="mdc-touch-target-wrapper">


			<button class="mdc-button mdc-button--raised" on:click={addPerson}>
				<span class="mdc-button__ripple"></span>
				<span class="mdc-button__touch"></span>
				<span class="mdc-button__focus-ring"></span>
				<span class="mdc-button__label">Add Person</span>
			</button>
		</div>
	</div>
{:else if step === 'step_one'}
	<div id="step_one">
		<h3>Step 1: Basic Info</h3>
		Step 1: Basic Info<br />
		Step 2: Relationship<br />
		Step 3: Upload Docs<br />

		<ul>
			<li>First Name</li>
			<li>Middle Name (optional)</li>
			<li>Last Name</li>
			<li>Date of birth</li>
			<li>Birthplace</li>
			<li>Date of Death (optional)</li>
		</ul>
		<div class="mdc-touch-target-wrapper">
			<button class="mdc-button mdc-button--raised" on:click={stepOne}>
			<span class="mdc-button__ripple"></span>
			<span class="mdc-button__touch"></span>
			<span class="mdc-button__focus-ring"></span>
			<span class="mdc-button__label">Next</span>
			</button>
		</div>
	</div>
{:else if step === 'step_two'}

	<!-- TODO: add edit/pre-populate -->
	<div id="step_two">
		<h3>Step 2: Relationship</h3>
		Step 1: Basic Info<br />
		Step 2: Relationship<br />
		Step 3: Upload Docs<br />

		<h4>Biological</h4> 
		<ul>
			<li>Mother</li>
				<li>First Name</li>
				<li>Middle Name (optional)</li>
				<li>Last Name</li>
				<li>Date of birth</li>
				<li>Birthplace</li>
				<li>Date of Death (optional)</li>
		  </ul>
		  <ul>
			<li>Father</li>
				<li>First Name</li>
				<li>Middle Name (optional)</li>
				<li>Last Name</li>
				<li>Date of birth</li>
				<li>Birthplace</li>
				<li>Date of Death (optional)</li>
		  </ul>
		<h4>Adopted</h4> 
		<ul>
			<li>Mother</li>
				<li>First Name</li>
				<li>Middle Name (optional)</li>
				<li>Last Name</li>
				<li>Date of birth</li>
				<li>Birthplace</li>
				<li>Date of Death (optional)</li>
		  </ul>
		  <ul>
			<li>Father</li>
				<li>First Name</li>
				<li>Middle Name (optional)</li>
				<li>Last Name</li>
				<li>Date of birth</li>
				<li>Birthplace</li>
				<li>Date of Death (optional)</li>
		  </ul>
		  <div class="mdc-touch-target-wrapper">
			<button class="mdc-button mdc-button--raised" on:click={stepTwo}>
			<span class="mdc-button__ripple"></span>
			<span class="mdc-button__touch"></span>
			<span class="mdc-button__focus-ring"></span>
			<span class="mdc-button__label">Next</span>
			</button>
		</div>
	</div>

{:else if step === 'step_three'}
	<div id="step_three">
		<h3>Step 3: Upload Docs</h3>
		Step 1: Basic Info<br />
		Step 2: Relationship<br />
		Step 3: Upload Docs<br />

		<h4>Required</h4> 
		<ul>
			<li>Birth Certificate</li>
			<li>If no birth certificate, allow for other types of documentation</li>
		</ul>
		<h4>Optional</h4> 
		<ul>
			<li>Any kine you like</li>
		</ul>
		<form>
			<input type="file" id="support_doc" name="support_doc">
		</form>
		<div class="mdc-touch-target-wrapper">
			<button class="mdc-button mdc-button--raised"  on:click={stepThree}>
			<span class="mdc-button__ripple"></span>
			<span class="mdc-button__touch"></span>
			<span class="mdc-button__focus-ring"></span>
			<span class="mdc-button__label">Finish</span>
			</button>
		</div>
	</div>
{/if}
