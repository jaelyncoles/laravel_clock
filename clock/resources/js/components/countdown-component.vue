<template>
  <div class="container">
    <div class="row justify-content-center">
          
          <div class="content">
            <div id="txt" class="display-1">{{h}}:{{m}}:{{s}}</div>
          </div>
        </div>
      </div>
</template>

<script>
export default {
  name: "countdown-component",
  data() {
    return {
      h: 0,
      m: 0,
	  s: 0,
	  interval: null
    };
  },
  methods: {
    startTime: function() {
	  
	  var self = this;
	  console.log(this);
	  // var t = setInterval(this.startTime(), 1000);  // this is relative to setInterval
      this.interval = setInterval(() => {
		  console.log(this);
		  var today = new Date();
			this.h = today.getHours();
			self.m = today.getMinutes();
			self.s = today.getSeconds();
			
			self.m = self.checkTime(self.m);
			self.s = self.checkTime(self.s);
	  }, 1000);
    },

    checkTime: function(i) {
      if (i < 10) {
        i = "0" + i;
	  } // add zero in front of numbers < 10
	  
	  console.log("zero please");
      return i;
    }
  },
  mounted: function() {
    this.startTime();
  }
};
</script>