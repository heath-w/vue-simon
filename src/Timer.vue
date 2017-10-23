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
	      intervalId: null
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
	  	startTimer: function( timerLength ) {
	  		if ( this.intervalId === null ) {
	  			this.message = '';
	  			this.remaining = timerLength;
	  			this.intervalId = window.setInterval( this.tick, 1000 );
	  		}
	  		else { }	  		
	  	},

	  	stopTimer: function( text ) {
	  		window.clearInterval( this.intervalId );
	  		this.intervalId = null;
	  		this.remaining = '';
	  		if ( text ) {
	  			this.message = text;	
	  		}
	  		else {
	  			this.message = '';
	  		}	  		
	  	},	  	

	  	tick: function() {
	  		console.log( 'tick (Spoon!)' );
	  		this.remaining -= 1;	  	
	  		if ( this.remaining === 0 ) {
	  			this.$bus.$emit( 'expired' );
	  			window.clearInterval( this.intervalId );
	  			this.intervalId = null;
	  		}	
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