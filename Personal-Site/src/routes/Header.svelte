<script>
import { onMount } from 'svelte/internal';
	let header;
	onMount(() => {
		let header = document.querySelector('#intro-header');
		let anim = [
  { t: "{ }", ms: 400 },
  { t: "{ }", ms: 400 },
  { t: "{_}", ms: 400 },
  { t: "{I_}", ms: 200 },
  { t: "{IR_}", ms: 200 },
  { t: "{IRV_}", ms: 200 },
  { t: "{IRVY_}", ms: 200 },
  { t: "{IRVYN}", ms: 200 },
  { t: "{IRVYN}", ms: 200 }
];

  let stepDenominator = 1;
  if (window.localStorage.stepDenominator)
      stepDenominator = window.localStorage.stepDenominator;
  let i = 0;
  let update = () => {
      let step = anim[i];
      header.innerText = step.t;
      i++;

      if (i < anim.length)
          setTimeout(update, step.ms / stepDenominator);
      else {
          header.classList.add('top');
          header.style.top = '50%';
          header.style.left = '50%';
          header.style.transform = 'translate(-50%, -50%)';
          setTimeout(() => {
              header.classList.add('move-to-top-middle');
          }, 500);
		  header.style.top = '0';
			header.style.left = '50%';
			header.style.transform = 'translate(-50%, -55%) scale(0.55)';

		  	// shows content after the animation
			const footer = document.querySelector('footer');
			const main = document.querySelector('main');
			const hr = document.querySelector('hr');

			main.classList.remove('slot-content');
			footer.classList.remove('footer-content');
			hr.classList.remove('footer-content');

          window.localStorage.stepDenominator = 2;
      }
  }
  update();
	});
		
</script>
	<h1 id="intro-header">

	</h1>
<style>
	
	h1 {
		font-family: 'Playfair Display', serif;
		font-size: 64px;
		font-weight: bold;
		text-align: center;
		color: black;
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
	}
	
	#intro-header {
	transition: all 1s ease-out;
	font-family: 'inconsolata', monospace;
	}
</style>