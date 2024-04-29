<script>
 var countDownDate = new Date("May 29, 2024 00:00:00").getTime();

// Update the count down every 1 second
var x = setInterval(function() {

  // Get today's date and time
  var now = new Date().getTime();

  // Find the distance between now and the count down date
  var distance = countDownDate - now;

  // Time calculations for days, hours, minutes and seconds
  var days = Math.floor(distance / (1000 * 60 * 60 * 24));
  var hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
  var minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
  var seconds = Math.floor((distance % (1000 * 60)) / 1000);

  // Display the result in the element with id="demo"
  document.getElementById("days").innerHTML = days
  document.getElementById("hours").innerHTML = hours
  document.getElementById("minutes").innerHTML = minutes
  document.getElementById("seconds").innerHTML = seconds

  // If the count down is finished, write some text
  if (distance < 0) {
    clearInterval(x);
    document.getElementById("demo").innerHTML = "EXPIRED";
  }
}, 1000);
</script>
<template>
<div class="w-[85%] h-[90vh] mx-auto flex items-center gap-3 flex-col justify-center text-black">
    <h1 class="text-3xl font-semibold">Auksion boshlanishiga:</h1>
    <div class="flex gap-4 items-center justify-center">
        <div class="flex items-center justify-center flex-col">
            <p id="days" class="text-7xl text-green-600"></p>
            <span>Kun</span>
        </div>
        <span class="text-3xl">:</span>

        <div class="flex items-center justify-center flex-col">
            <p id="hours" class="text-7xl text-green-600"></p>
            <span>Soat</span>
        </div>
                <span class="text-3xl">:</span>
        <div class="flex items-center justify-center flex-col">
            <p id="minutes" class="text-7xl text-green-600"></p>
            <span>Daqiqa</span>
        </div>
                <span class="text-3xl">:</span>
        <div class="flex items-center justify-center flex-col">
            <p id="seconds" class="text-7xl text-green-600"></p>
            <span>Soniya</span>
        </div>
    </div>
</div>
</template>