// Timer.vue

<template>

	<div id="status">
		<p>
			{{ message }}{{ remaining }}
		</p>
	</div>

</template>

<script>

	export default {
	  name: 'timer',

	  data () {
	    return {
	      message: 'Click the start button to begin!',
	      remaining: '',
	    }
	  },

	  created() {
	  	this.$bus.$on( 'stateChange', ( $event, timerLength ) => {
	  		switch( $event ) {
	  			case 'capturing':
	  				this.startTimer( timerLength );
	  				break;
	  			case 'playing':
	  				this.stopTimer( 'Watch closely...' );
	  				break;	
	  			case 'processing':
	  				this.stopTimer();
	  				break;
	  			case 'gameover':
	  				this.stopTimer( 'Oops! Click the start button to play again.' );
	  				break;
	  			default:
	  				console.log( 'created: event state unknown: ', $event );	
	  		}
	  	} );
	  },

	  methods: {
	  	startTimer: function() {

	  		setInterval( this.tick, 1000 );
	  	},
	  	stopTimer: function() {},	  	
	  	tick: function() {
	  		console.log( 'tick' );
	  	}
	  }
	}

</script>	

<style>
	#status {
		height: 40px;
		color: #999;
		font-weight: bold;
	}
</style>