<script context="module">
	export const prerender = true;
</script>

<script>
	let state = {
		scene: '2ce',
		el: 1,
		door: 0,
		walk: 0,
		power: 0,
		ladder: 1,
		switch: 0,
		keypad: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
		keylock: 0,
		winState: 0,
		music: 0,
		story: 4
	};

	const text1 =
		'Fact: There is a house in Brooklyn that is not a house. The windows are blackened. No one is home. It is a New York City subway vent, disguised as a house. This is 58 Joralemon Street.';

	const text2 =
		'Not-so-Fact: There has been a service emergency on the Metropolitan Transit Authority. The entire system is on the fritz. Every subway line is experiencing severe delays. The mayor is baffled. Nobody can figure out what is going on.';

	const text3 =
		'Except you. Your job is to enter 58 Joralemon, figure out the controls to the system, and get the trains back on track. The city is counting on you.';

	const text4 =
		'Hurray! You saved the day! The citizens of New York City thank you greatly. Your job here is done.';

	const text5 = 'Until next time...';

	const text6 = '-Ben Tupper';

	const imageNames = [
		'Op1',
		'Op2',
		'Op3',
		'En1',
		'En2',
		'En3',
		'0ae-el0-walk0',
		'0ae-el0-walk1',
		'0ae-el1-walk0',
		'0ae-el1-walk1',
		'0ae-el2-walk0',
		'0ae-el2-walk1',
		'0an',
		'0as-el0-walk0-ladder0',
		'0as-el0-walk0-ladder1',
		'0as-el0-walk1-ladder0',
		'0as-el0-walk1-ladder1',
		'0as-el1-walk0-ladder0',
		'0as-el1-walk0-ladder1',
		'0as-el1-walk1-ladder0',
		'0as-el1-walk1-ladder1',
		'0as-el2-walk0-ladder0',
		'0as-el2-walk0-ladder1',
		'0as-el2-walk1-ladder0',
		'0as-el2-walk1-ladder1',
		'0au',
		'0aw-power0',
		'0aw-power1',
		'0be-el0-walk0',
		'0be-el0-walk1',
		'0be-el1-walk0',
		'0be-el1-walk1',
		'0be-el2-walk0',
		'0be-el2-walk1',
		'0bn-walk0-power0',
		'0bn-walk0-power1',
		'0bn-walk1-power0',
		'0bn-walk1-power1',
		'0bs-ladder0',
		'0bs-ladder1',
		'0bu-ladder0',
		'0bu-ladder1',
		'0bw',
		'0ce-el0-door0',
		'0ce-el0-door1',
		'0ce-el1',
		'0ce-el2-door0',
		'0cn',
		'0cs',
		'0cw-walk1-power0-ladder0',
		'0cw-walk1-power0-ladder1',
		'0cw-walk1-power1-ladder0',
		'0cw-walk1-power1-ladder1',
		'0de',
		'0dn',
		'0ds',
		'0dw-power0-ladder0',
		'0dw-power0-ladder1',
		'0dw-power1-ladder0',
		'0dw-power1-ladder1',
		'0dw',
		'0le',
		'0ln',
		'0ls-power0',
		'0ls-power1',
		'0lw-door0-ladder0',
		'0lw-door0-ladder1',
		'0lw-door1-walk0-ladder0',
		'0lw-door1-walk0-ladder1',
		'0lw-door1-walk1-ladder0',
		'0lw-door1-walk1-ladder1',
		'0lz',
		'1ae',
		'1an',
		'1as-el0-walk0-ladder0',
		'1as-el0-walk0-ladder1',
		'1as-el0-walk1-ladder0',
		'1as-el0-walk1-ladder1',
		'1as-el1-walk0-ladder0',
		'1as-el1-walk0-ladder1',
		'1as-el1-walk1-ladder0',
		'1as-el1-walk1-ladder1',
		'1as-el2-walk0-ladder0',
		'1as-el2-walk0-ladder1',
		'1as-el2-walk1-ladder0',
		'1as-el2-walk1-ladder1',
		'1aw-walk0-ladder0',
		'1aw-walk0-ladder1',
		'1aw-walk1-ladder0',
		'1aw-walk1-ladder1',
		'1bd-power0-walk0',
		'1bd-power0-walk1',
		'1bd-power1-walk0',
		'1bd-power1-walk1',
		'1be-el0-walk0',
		'1be-el0-walk1',
		'1be-el1-walk0',
		'1be-el1-walk1',
		'1be-el2-walk0',
		'1be-el2-walk1',
		'1bn',
		'1bs-el0-ladder0',
		'1bs-el0-ladder1',
		'1bs-el1-ladder0',
		'1bs-el1-ladder1',
		'1bs-el2-ladder0',
		'1bs-el2-ladder1',
		'1bw',
		'1ce',
		'1cn-power0',
		'1cn-power1',
		'1cs-el0-door0',
		'1cs-el1-door0',
		'1cs-el1-door1-power0',
		'1cs-el1-door1-power1',
		'1cs-el2-door0',
		'1cw-walk0-power0-ladder0',
		'1cw-walk0-power0-ladder1',
		'1cw-walk0-power1-ladder0',
		'1cw-walk0-power1-ladder1',
		'1cw-walk1-power0-ladder0',
		'1cw-walk1-power0-ladder1',
		'1cw-walk1-power1-ladder0',
		'1cw-walk1-power1-ladder1',
		'1de',
		'1dn-walk0-power0',
		'1dn-walk0-power1',
		'1dn-walk1-power0',
		'1dn-walk1-power1',
		'1ds',
		'1dw-walk0-power0-ladder0',
		'1dw-walk0-power0-ladder1',
		'1dw-walk0-power1-ladder0',
		'1dw-walk0-power1-ladder1',
		'1dw-walk1-power0-ladder0',
		'1dw-walk1-power0-ladder1',
		'1dw-walk1-power1-ladder0',
		'1dw-walk1-power1-ladder1',
		'1le',
		'1ln-door0',
		'1ln-door1-walk0',
		'1ln-door1-walk1',
		'1ls-power0',
		'1ls-power1',
		'1lw-door0',
		'1lw-door1',
		'1lz',
		'2ae-el0',
		'2ae-el1',
		'2ae-el2-door0',
		'2ae-el2-door1',
		'2an',
		'2as',
		'2aw-ladder0',
		'2aw-ladder1',
		'2bd-ladder0',
		'2bd-ladder1',
		'2be-el0',
		'2be-el1',
		'2be-el2',
		'2bn',
		'2bs-ladder0',
		'2bs-ladder1',
		'2bw',
		'2ce-door0',
		'2ce-door0',
		'2ce-door1-switch0',
		'2ce-door1-switch1',
		'2ce-door1-switch0',
		'2cn',
		'2cs',
		'2cw-ladder0',
		'2cw-ladder1',
		'2le',
		'2ln-door0',
		'2ln-door1',
		'2ls-power0',
		'2ls-power1',
		'2lw-door0-ladder0',
		'2lw-door0-ladder1',
		'2lw-door1-ladder0',
		'2lw-door1-ladder1',
		'2lz',
		'Fas',
		'Fbs-door0',
		'Fbs-door1',
		'Fcs-door0',
		'Fcs-door1'
	];

	function updateState() {
		state = state;
		console.log(state);
	}

	const forwardScene = {
		'0dw': '0cw',
		'0cw': '0bw',
		'0an': 'Fas',
		'1as': '1cs',
		'1aw': '1bw',
		'1be': '1ae',
		'1cn': '1an',
		'2aw': '2bw',
		'2be': '2ae',
		'2cw': '2aw'
	};

	const noTurns = [
		'0bu',
		'Fas',
		'Fbs',
		'Fcs',
		'1bd',
		'2bs',
		'2ce',
		'2bd',
		'0lz',
		'1lz',
		'2lz',
		'0au'
	];

	let specialButtons = [
		{
			name: 'Fas',
			conditions: true,
			button: {
				style: 'top: 30%; left: 0; height: 70%; width: 40%; cursor: n-resize;',
				click: () => {
					state.scene = 'Fbs';
				}
			}
		},

		{
			name: 'Fas',
			conditions: true,
			button: {
				style: 'top: 50%; left: 50%; height: 50%; width: 50%; cursor:  n-resize;',
				click: () => {
					state.scene = 'Fcs';
				}
			}
		},

		{
			name: 'Fbs',
			conditions: true,
			button: {
				class: 'left',
				style: 'width: 10%',
				click: () => {
					(state.scene = 'Fas'), (state.door = 0);
				}
			}
		},

		{
			name: 'Fbs',
			conditions: true,
			button: {
				class: 'right',
				style: 'left: 90%; width: 10%',
				click: () => {
					(state.door = 0), (state.scene = 'Fas');
				}
			}
		},

		{
			name: 'Fbs',
			conditions: { door: 0 },
			button: {
				style: 'top: 12%; left: 20%; height: 80%; width: 56%; cursor:  pointer;',
				click: () => {
					playEffect('front', 0.3);
					state.door = 1;
				}
			}
		},

		{
			name: 'Fbs',
			conditions: { door: 1 },
			button: {
				class: 'right',
				style: 'top: 12%; left: 20%; height: 80%; width: 56%; cursor:  n-resize;',
				click: () => {
					state.scene = '1as';
					if (!state.music) {
						playMusic('music');
						state.music = 1;
					}
				}
			}
		},

		{
			name: 'Fcs',
			conditions: { door: 0 },
			button: {
				style: 'top: 12%; left: 20%; height: 80%; width: 56%; cursor:  n-resize;',
				click: () => {
					playEffect('cellar', 0.3);
					state.door = 1;
				}
			}
		},

		{
			name: 'Fcs',
			conditions: { door: 1 },
			button: {
				style: 'top: 0; height: 100%; left: 20%; width: 60%; cursor: n-resize;',
				click: () => {
					if (!state.music) {
						playMusic('music');
						state.music = 1;
					}

					(state.scene = '0as'), (state.door = 0);
				}
			}
		},

		{
			name: 'Fcs',
			conditions: true,
			button: {
				class: 'left',
				style: 'width: 10%',
				click: () => {
					(state.door = 0), (state.scene = 'Fas');
				}
			}
		},

		{
			name: 'Fcs',
			conditions: true,
			button: {
				class: 'right',
				style: 'left: 90%; width: 10%',
				click: () => {
					(state.door = 0), (state.scene = 'Fas');
				}
			}
		},

		{
			name: '0as',
			conditions: { walk: 1 },
			button: {
				class: 'forward',
				click: () => {
					state.scene = '0bs';
				}
			}
		},

		{
			name: '0aw',
			conditions: true,
			button: {
				class: 'up',
				click: () => {
					state.scene = '0au';
				}
			}
		},

		{
			name: '0aw',
			conditions: { power: 0 },
			button: {
				style: 'top: 33%; height: 31%; left: 36%; width: 35%; cursor: pointer;',
				click: () => {
					state.power = 1;
					playEffect('power', 0.6);
				}
			}
		},

		{
			name: '0aw',
			conditions: { power: 1 },
			button: {
				style: 'top: 18%; height: 27%; left: 36%; width: 35%; cursor: pointer;',
				click: () => {
					state.power = 0;
					playEffect('power', 0.6);
				}
			}
		},

		{
			name: '0au',
			conditions: true,
			button: {
				style: 'top: 60%; height: 40%; left: 0; width: 100%; cursor: s-resize',
				click: () => {
					state.scene = '0aw';
				}
			}
		},

		{
			name: '0bs',
			conditions: true,
			button: {
				class: 'up',
				style: 'background-color: green',
				click: () => {
					state.scene = '0bu';
				}
			}
		},

		{
			name: '0be',
			conditions: { walk: 1 },
			button: {
				class: 'forward',
				click: () => {
					state.scene = '0ce';
				}
			}
		},

		{
			name: '0bn',
			conditions: { walk: 1 },
			button: {
				class: 'forward',
				click: () => {
					state.scene = '0an';
				}
			}
		},

		{
			name: '0bu',
			conditions: true,
			button: {
				style: 'top: 50%; height: 50%; left: 0; width: 100%; cursor: s-resize',
				click: () => {
					state.scene = '0bs';
				}
			}
		},

		{
			name: '0bu',
			conditions: { ladder: 0 },
			button: {
				class: 'forward',
				click: () => {
					state.scene = '2bs';
				}
			}
		},

		{
			name: '0ce',
			conditions: { el: 0, door: 0 },
			button: {
				style: 'top: 44%; height: 34%; left: 24%; width: 20%; cursor: pointer',
				click: () => {
					state.door = 1;
					playEffect('eldoor', 0.3);
				}
			}
		},

		{
			name: '0ce',
			conditions: { el: 0, door: 1 },
			button: {
				style: 'top: 0; height: 100%; left: 25%; width: 50%; cursor: n-resize;',
				click: () => {
					state.scene = '0le';
				}
			}
		},

		{
			name: '0ce',
			conditions: { el: 1 },
			button: {
				style: 'top: 0; height: 100%; left: 25%; width: 50%; cursor: n-resize;',
				click: () => {
					state.scene = '0de';
				}
			}
		},

		{
			name: '0ce',
			conditions: { el: 2 },
			button: {
				style: 'top: 0; height: 100%; left: 25%; width: 50%; cursor: n-resize;',
				click: () => {
					state.scene = '0de';
				}
			}
		},

		{
			name: '0ce',
			conditions: { el: 0, door: 1 },
			button: {
				style: 'top: 41%; height: 37%; left: 81%; width: 19%; cursor: pointer',
				click: () => {
					state.door = 0;
					playEffect('eldoor', 0.3);
				}
			}
		},

		{
			name: '0lw',
			conditions: { door: 1, walk: 1 },
			button: {
				style: 'top:0; height: 100%; left: 25%; width:50%',
				click: () => {
					state.scene = '0cw';
				}
			}
		},

		{
			name: '1an',
			conditions: true,
			button: {
				style: 'top:0; height: 100%; left: 25%; width:50%',
				click: () => {
					state.scene = 'Fas';
				}
			}
		},

		{
			name: '1bs',
			conditions: true,
			button: {
				class: 'down',
				click: () => {
					state.scene = '1bd';
				}
			}
		},

		{
			name: '1bd',
			conditions: true,
			button: {
				class: 'left',
				style: 'width: 10%; cursor: s-resize',
				click: () => {
					state.scene = '1bs';
				}
			}
		},

		{
			name: '1bd',
			conditions: true,
			button: {
				class: 'right',
				style: 'left: 90%; width: 10%; cursor: s-resize;',
				click: () => {
					state.scene = '1bs';
				}
			}
		},

		{
			name: '1bd',
			conditions: true,
			button: {
				class: 'up',
				style: 'left: 10%; width: 80%; 	cursor: s-resize;',
				click: () => {
					state.scene = '1bs';
				}
			}
		},

		{
			name: '1bd',
			conditions: true,
			button: {
				style: 'top: 56%; left: 14%; height: 44%; width: 73%; cursor: pointer;',
				click: () => {
					if (state.power) {
						state.walk = state.walk ? 0 : 1;
						playEffect('wheel_power1', 0.2);
					} else {
						playEffect('wheel_power0', 0.1);
					}
				}
			}
		},

		{
			name: '1cs',
			conditions: { el: 0 },
			button: {
				style: 'top: 0; left: 25%; height: 100%; width: 50%; cursor: pointer;',
				click: () => {
					state.scene = '1ds';
				}
			}
		},

		{
			name: '1dn',
			conditions: { el: 0 },
			button: {
				style: 'top: 0; left: 25%; height: 100%; width: 50%; cursor: pointer;',
				click: () => {
					state.scene = '1cn';
				}
			}
		},

		{
			name: '1cs',
			conditions: { el: 1, door: 0 },
			button: {
				style: 'top: 42%; left: 54%; height: 44%; width: 25%; cursor: pointer;',
				click: () => {
					state.door = 1;
					playEffect('eldoor', 0.3);
				}
			}
		},

		{
			name: '1cs',
			conditions: { el: 1, door: 1 },
			button: {
				class: 'forward',
				click: () => {
					state.scene = '1ls';
				}
			}
		},

		{
			name: '1ls',
			conditions: true,
			button: {
				class: 'elevator-button',
				click: () => {
					if (state.power) {
						(state.scene = '2ls'), (state.el = 2);
						playEffect('elbutton_power1', 0.12);
					} else {
						playEffect('elbutton_power0', 0.05);
					}
				}
			}
		},

		{
			name: '1ls',
			conditions: true,
			button: {
				class: 'elevator-button',
				style: 'top: 70%;',
				click: () => {
					if (state.power) {
						(state.scene = '1ls'), (state.el = 1);
					} else {
						playEffect('elbutton_power0', 0.05);
					}
				}
			}
		},

		{
			name: '1ls',
			conditions: true,
			button: {
				class: 'elevator-button',
				style: 'top: 80%;',
				click: () => {
					if (state.power) {
						(state.scene = '0ls'), (state.el = 0);
						playEffect('elbutton_power1', 0.12);
					} else {
						playEffect('elbutton_power0', 0.05);
					}
				}
			}
		},

		{
			name: '1ln',
			conditions: { door: 1 },
			button: {
				style: 'top:0; height: 100%; left: 25%; width:50%',
				click: () => {
					state.scene = '1cn';
				}
			}
		},

		{
			name: '2ls',
			conditions: true,
			button: {
				class: 'elevator-button',
				click: () => {
					if (state.power) {
						(state.scene = '2ls'), (state.el = 2);
					} else {
						playEffect('elbutton_power0', 0.05);
					}
				}
			}
		},

		{
			name: '2ls',
			conditions: true,
			button: {
				class: 'elevator-button',
				style: 'top: 70%;',
				click: () => {
					if (state.power) {
						(state.scene = '1ls'), (state.el = 1);
						playEffect('elbutton_power1', 0.12);
					} else {
						playEffect('elbutton_power0', 0.05);
					}
				}
			}
		},

		{
			name: '2ls',
			conditions: true,
			button: {
				class: 'elevator-button',
				style: 'top: 80%;',
				click: () => {
					if (state.power) {
						(state.scene = '0ls'), (state.el = 0);
						playEffect('elbutton_power1', 0.12);
					} else {
						playEffect('elbutton_power0', 0.05);
					}
				}
			}
		},

		{
			name: '0ls',
			conditions: true,
			button: {
				class: 'elevator-button',
				click: () => {
					if (state.power) {
						(state.scene = '2ls'), (state.el = 2);
						playEffect('elbutton_power1', 0.12);
					} else {
						playEffect('elbutton_power0');
					}
				}
			}
		},

		{
			name: '0ls',
			conditions: true,
			button: {
				class: 'elevator-button',
				style: 'top: 70%;',
				click: () => {
					if (state.power) {
						(state.scene = '1ls'), (state.el = 1);
						playEffect('elbutton_power1', 0.12);
					} else {
						playEffect('elbutton_power0', 0.05);
					}
				}
			}
		},

		{
			name: '0ls',
			conditions: true,
			button: {
				class: 'elevator-button',
				style: 'top: 80%;',
				click: () => {
					if (state.power) {
						(state.scene = '0ls'), (state.el = 0);
					} else {
						playEffect('elbutton_power0', 0.05);
					}
				}
			}
		},

		{
			name: '0lw',
			conditions: { door: 0 },
			button: {
				class: 'elevator-door',
				click: () => {
					state.door = 1;
					playEffect('eldoor', 0.3);
				}
			}
		},

		{
			name: '0lw',
			conditions: { door: 1 },
			button: {
				class: 'elevator-door',
				style: 'left: 15%;',
				click: () => {
					playEffect('eldoor', 0.3);
					state.door = 0;
				}
			}
		},

		{
			name: '1ln',
			conditions: { door: 0 },
			button: {
				class: 'elevator-door',
				style: 'left: 10%;',
				click: () => {
					playEffect('eldoor', 0.3);
					state.door = 1;
				}
			}
		},

		{
			name: '1ln',
			conditions: { door: 1 },
			button: {
				class: 'elevator-door',
				style: 'left: 67%; width: 15%;',
				click: () => {
					playEffect('eldoor', 0.3);
					state.door = 0;
				}
			}
		},

		{
			name: '2lw',
			conditions: { door: 0 },
			button: {
				class: 'elevator-door',
				click: () => {
					state.door = 1;
					playEffect('eldoor', 0.3);
				}
			}
		},

		{
			name: '2lw',
			conditions: { door: 1 },
			button: {
				class: 'forward',
				click: () => {
					state.scene = '2aw';
				}
			}
		},

		{
			name: '2lw',
			conditions: { door: 1 },
			button: {
				class: 'elevator-door',
				style: 'left: 15%;',
				click: () => {
					playEffect('eldoor', 0.3);
					state.door = 0;
				}
			}
		},

		{
			name: '2bs',
			conditions: true,
			button: {
				style: 'top: 0; height: 100%; left: 0; width: 15%; cursor: w-resize',
				click: () => {
					state.scene = '2be';
				}
			}
		},

		{
			name: '2bs',
			conditions: true,
			button: {
				class: 'right',
				style: 'height: 25%; left: 77%; width: 23%; cursor: e-resize;',
				click: () => {
					state.scene = '2bw';
				}
			}
		},

		{
			name: '2bs',
			conditions: true,
			button: {
				class: 'right',
				style: 'top: 85%; height: 15%; left: 77%; width: 23%;',
				click: () => {
					state.scene = '2bw';
				}
			}
		},

		{
			name: '2bs',
			conditions: true,
			button: {
				style: 'top: 54%; height: 46%; left: 15%; width: 60%; cursor: s-resize',
				click: () => {
					state.scene = '2bd';
				}
			}
		},

		{
			name: '2bs',
			conditions: { ladder: 1 },
			button: {
				style: 'top: 30%; height: 31%; left: 77%; width: 21%; cursor: pointer',
				click: () => {
					state.ladder = 0;
					playEffect('power', 0.6);
				}
			}
		},

		{
			name: '2bs',
			conditions: { ladder: 0 },
			button: {
				style: 'top: 50%; height: 31%; left: 77%; width: 21%; cursor: pointer',
				click: () => {
					state.ladder = 1;
					playEffect('power', 0.6);
				}
			}
		},

		{
			name: '2ae',
			conditions: { el: 1 },
			button: {
				class: 'forward',
				click: () => {
					state.scene = '2ce';
				}
			}
		},

		{
			name: '2ce',
			conditions: { winState: 0 },
			button: {
				class: 'left',
				style: 'top: 0; height: 100%; left: 0; width: 20%',
				click: () => {
					state.scene = '2cn';
				}
			}
		},

		{
			name: '2ce',
			conditions: { winState: 0 },
			button: {
				class: 'right',
				style: 'height: 70%; left: 85%; width: 15%',
				click: () => {
					state.scene = '2cs';
				}
			}
		},

		{
			name: '2bd',
			conditions: true,
			button: {
				style: 'top: 0; height: 25%; left: 0; width: 100%; cursor: n-resize',
				click: () => {
					state.scene = '2bs';
				}
			}
		},

		{
			name: '2bd',
			conditions: { ladder: 0 },
			button: {
				style: 'top: 25%; height: 67%; left: 10%; width: 83%; cursor: s-resize',
				click: () => {
					state.scene = '0bs';
				}
			}
		},

		{
			name: '2ae',
			conditions: { el: 2, door: 0 },
			button: {
				style: 'top: 41%; height: 37%; left: 20%; width: 20%; cursor: pointer',
				click: () => {
					playEffect('eldoor', 0.3);
					state.door = 1;
				}
			}
		},

		{
			name: '2ae',
			conditions: { el: 2, door: 1 },
			button: {
				style: 'top: 0; height: 100%; left: 25%; width: 50%; cursor: pointer',
				click: () => {
					state.scene = '2le';
				}
			}
		},

		{
			name: '2ae',
			conditions: { el: 2, door: 1 },
			button: {
				style: 'top: 41%; height: 37%; left: 65%; width: 20%; cursor: pointer',
				click: () => {
					state.door = 0;
					playEffect('eldoor', 0.3);
				}
			}
		},

		{
			name: '1cs',
			conditions: { el: 1, door: 1 },
			button: {
				style: 'top: 41%; height: 37%; left: 6%; width: 20%; cursor: pointer',
				click: () => {
					state.door = 0;
					playEffect('eldoor', 0.3);
				}
			}
		},

		{
			name: '2ce',
			conditions: { keylock: 0 },
			button: {
				style: 'top: 83%; height: 17%; left: 83%; width: 13%; cursor: pointer',
				click: () => {
					state.keypad = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0];
					playEffect('elbutton_power0', 0.05);
				}
			}
		},

		{
			name: '2ce',
			conditions: { keylock: 1, winState: 0 },
			button: {
				style: 'top: 83%; height: 17%; left: 83%; width: 13%; cursor: pointer',
				click: () => {
					state.door = 1;
					state.keypad = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0];
					playEffect('eldoor', 0.3);
				}
			}
		},

		{
			name: '2ce',
			conditions: { door: 1, switch: 0 },
			button: {
				style: 'top: 46%;    height: 30%;    left: 43%;    width: 20%;    cursor: pointer;',
				click: () => {
					state.switch = 1;
					state.winState = 'fade-out';
					playEffect('power', 0.6);
					playEffect('train', 0.15);
					setTimeout(function () {
						state.story += 1;
						console.log(state.story);
					}, 6000);
				}
			}
		},

		{
			name: '2ln',
			conditions: { door: 0 },
			button: {
				style: 'top: 76%; height: 24%; left: 30%; width: 18%; cursor: zoom-in;',
				click: () => {
					state.scene = '2lz';
				}
			}
		},

		{
			name: '1ln',
			conditions: { door: 0 },
			button: {
				style: 'top: 76%; height: 24%; left: 30%; width: 18%; cursor: zoom-in;',
				click: () => {
					state.scene = '1lz';
				}
			}
		},

		{
			name: '0ln',
			conditions: { door: 0 },
			button: {
				style: 'top: 76%; height: 24%; left: 30%; width: 18%; cursor: zoom-in;',
				click: () => {
					state.scene = '0lz';
				}
			}
		},

		{
			name: '0lz',
			conditions: { door: 0 },
			button: {
				style: 'top: 0; height: 100%; left: 0; width: 100%; cursor: zoom-out;',
				click: () => {
					state.scene = '0ln';
				}
			}
		},

		{
			name: '1lz',
			conditions: { door: 0 },
			button: {
				style: 'top: 0; height: 100%; left: 0; width: 100%; cursor: zoom-out;',
				click: () => {
					state.scene = '1ln';
				}
			}
		},

		{
			name: '2lz',
			conditions: { door: 0 },
			button: {
				style: 'top: 0; height: 100%; left: 0; width: 100%; cursor: zoom-out;',
				click: () => {
					state.scene = '2ln';
				}
			}
		}
	];

	function playEffect(filename, volume = 1) {
		const audio1 = new Audio(`sounds/${filename}.mp3`);
		audio1.volume = volume * 0.8;

		audio1.play();
	}

	function playMusic(filename, volume = 1) {
		const audio2 = new Audio(`sounds/${filename}.mp3`);
		audio2.volume = volume * 0.5;
		audio2.loop = true;
		audio2.play();
	}

	function changeState(state, buttonType) {
		state.door = 0;
		if (['left', 'right'].includes(buttonType)) {
			state.scene = turnScene(state, buttonType);
		} else if (buttonType === 'forward') {
			state.scene = forwardScene[state.scene];
		} else {
			state.scene = buttonType;
		}
		updateState();
	}

	function turnScene(state, newButton) {
		let directions = ['n', 'e', 's', 'w', 'n'];
		const ab = state.scene.slice(0, 2);
		const c = state.scene.slice(2, 3);
		if (newButton === 'left') {
			directions.reverse();
		}
		let i = directions.findIndex((y) => y === c);
		return ab + directions[i + 1];
	}

	function checkConditions(conditions) {
		for (const i of Object.keys(conditions)) {
			if (state[i] != conditions[i]) {
				return false;
			}
		}
		return true;
	}

	function findImage(state) {
		for (const img of imageNames) {
			let con = {};
			const splitLong = img.split('-');
			con['scene'] = splitLong[0];
			for (const i of splitLong.slice(1)) {
				con[i.slice(0, -1)] = i.slice(-1);
			}
			if (checkConditions(con)) {
				return 'images/' + img + '.jpg';
			}
		}
	}

	function findButtons(state) {
		let buttonList = [];

		// Insert forward buttons
		if (state.scene in forwardScene) {
			buttonList.push({ class: 'forward', click: () => changeState(state, 'forward') });
		}

		// Insert turning buttons
		if (!noTurns.includes(state.scene)) {
			buttonList.push(
				{ class: 'left', click: () => changeState(state, 'left') },
				{ class: 'right', click: () => changeState(state, 'right') }
			);
		}

		// Insert special buttons
		for (const s of specialButtons) {
			if (state.scene === s.name && checkConditions(s.conditions)) {
				buttonList.push(s['button']);
			}
		}

		return buttonList;
	}

	function compareList(a, b) {
		for (var i = 0; i < a.length; ++i) {
			if (a[i] !== b[i]) {
				console.log(state);
				console.log(false);
				return 0;
			}
		}
		console.log(true);
		console.log(state);
		return 1;
	}

	function editkeypad(i) {
		playEffect('keypad_buttons', 1);
		state.keypad[i] = state.keypad[i] ? 0 : 1;
		state.keylock = compareList(state.keypad, [0, 0, 1, 0, 1, 0, 0, 0, 1, 0, 0, 0]);
	}
</script>

<svelte:head>
	<title>Home</title>
</svelte:head>

{#if state.story < 4}
	<div class="text-container" on:click={((state.story += 1), updateState())}>
		{#if state.story >= 1}
			<div class="text" style="margin-top:8%">{text1}</div>
		{/if}
		{#if state.story >= 2}
			<div class="text" style="margin-top:30%">{text2}</div>
		{/if}
		{#if state.story >= 3}
			<div class="text" style="margin-top:55%">{text3}</div>
		{/if}
		<img src={findImage(state)} style="opacity: 0" />
	</div>
{/if}

{#if state.story >= 5}
	<div class="text-container" on:click={((state.story += 1), updateState())}>
		{#if state.story >= 5}
			<div class="text" style="margin-top:8%">{text4}</div>
		{/if}
		{#if state.story >= 6}
			<div class="text" style="margin-top:30%">{text5}</div>
		{/if}
		{#if state.story >= 7}
			<div class="text" style="margin-top:55%; margin-left: 55%">{text6}</div>
		{/if}
		<img src={findImage(state)} style="opacity: 0" />
	</div>
{/if}

{#if state.story === 4}
	<div class="image-container">
		<img src={findImage(state)} class={state.winState} />

		{#each findButtons(state) as newButton}
			<button
				id={newButton['id']}
				class={newButton['class']}
				style={newButton['style']}
				on:click={newButton['click']}
			/>
		{/each}

		{#if state.scene === '2ce' && state.door === 0}
			<div class="grid">
				{#each state.keypad as key, i}
					<div on:click={() => editkeypad(i)} class="grid-item" class:selected={state.keypad[i]} />
				{/each}
			</div>
		{/if}
	</div>
{/if}

<style>
	.grid {
		display: grid;
		position: absolute;
		top: 4%;
		left: 23%;
		width: 59%;
		height: 93%;
		grid-template-columns: 30% 36% 33%;
		grid-template-rows: 25.5% 26% 25% 23%;
		gap: 2px;
		cursor: pointer;
	}

	.grid-item {
		opacity: 0;
		background-color: black;
		transition: all 0.2s;
	}

	.grid-item.selected {
		opacity: 1;
	}

	img {
		width: 100%;
	}

	#testing {
		opacity: 0.5;
	}

	button {
		position: absolute;
		background-color: red;
		opacity: 0;
		cursor: n-resize;
		border: 0;
	}

	.left {
		top: 0;
		height: 100%;
		left: 0;
		width: 25%;
		cursor: w-resize;
	}

	.right {
		top: 0;
		height: 100%;
		left: 75%;
		width: 25%;
		cursor: e-resize;
	}

	.forward {
		top: 0;
		height: 100%;
		left: 25%;
		width: 50%;
	}

	.up {
		top: 0;
		height: 25%;
		left: 25%;
		width: 50%;
	}

	.down {
		top: 75%;
		height: 25%;
		left: 25%;
		width: 50%;
		cursor: s-resize;
	}

	.image-container {
		position: relative;
		width: 100%;
		background-color: black;
	}

	.text-container {
		position: relative;
		width: 100%;
		background-color: black;
	}

	.text {
		position: absolute;
		color: white;
		margin-left: 20%;
		margin-right: 20%;
		font-size: 1.5vw;
		font-family: 'Courier New', monospace;
		/* line-height: 1.4; */
	}

	.elevator-button {
		top: 60%;
		height: 9%;
		left: 47%;
		width: 12%;
		cursor: pointer;
	}

	.elevator-door {
		top: 60%;
		left: 54%;
		height: 40%;
		width: 25%;
		cursor: pointer;
	}

	.fade-out {
		visibility: visible;
		opacity: 0;
		transition: opacity 4s linear;
		transition-delay: 2s;
	}

	.fade-in {
		visibility: hidden;
		opacity: 0;
		transition: visibility 0s 2s, opacity 2s linear;
	}
</style>
