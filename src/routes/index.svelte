<svelte:head>
<link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Changa">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Hurricane&display=swap" rel="stylesheet">
<link href="https://fonts.googleapis.com/css2?family=Hurricane&family=Inspiration&display=swap" rel="stylesheet">
<link rel="preload" href="https://fonts.gstatic.com/s/quicksand/v7/6xKtdSZaM9iE8KbpRA_hK1QNYuDyPw.woff2" as="font" crossorigin>
<link rel="preload" href="https://fonts.gstatic.com/s/lato/v14/S6uyw4BMUTPHjx4wXiWtFCc.woff2" as="font" crossorigin>
</svelte:head>

<script>
	import { onMount } from 'svelte';
	let date = new Date(), month, day, year;
	let dateString1;
	let dateString2;
onMount(()=> {
        month = '' + (date.getMonth() + 1),
        day = '' + date.getDate(),
        year = date.getFullYear();
 
    if (month.length < 2) 
        month = '0' + month;
    if (day.length < 2) 
        day = '0' + day;

dateString1 = [year, month, day].join('-');
dateString2 = [year, month, day].join('-');
	})

         let days = 0;

	 function calculateDaysBetweenDates(begin, end) {
         let oneDay = 24*60*60*1000; // hours*minutes*seconds*milliseconds
         let firstDate = new Date(dateString1);
	 let secondDate = new Date(dateString2);
         days = Math.round(Math.abs((firstDate.getTime() - secondDate.getTime())/(oneDay)));
}
	//console.log(calculateDaysBetweenDates())
</script>

<h1> How many days from or until my next ...</h1>
<p> Use the date pickers then hit click to get the number of days between your two chosen dates.</p>



<label>
<input type=date bind:value={dateString1}>
<input type=date bind:value={dateString2}>
</label>

<button on:click={calculateDaysBetweenDates}>
	Click {days} 
</button>


<svelte:body />
<style>
@font-face {
 font-family: 'Lato';
 font-style: normal;
 font-weight: 400;
 src: local('Lato Regular'), local('Lato-Regular'), url(https://fonts.gstatic.com/s/lato/v14/S6uyw4BMUTPHjx4wXiWtFCc.woff2) format('woff2');
 unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD;
}
@font-face {
 font-family: 'Quicksand';
 font-style: normal;
 font-weight: 400;
 src: local('Quicksand Regular'), local('Quicksand-Regular'), url(https://fonts.gstatic.com/s/quicksand/v7/6xKtdSZaM9iE8KbpRA_hK1QNYuDyPw.woff2) format('woff2');
 unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD;
}
    h1 {
        font-family: 'Lato', cursive;
    }
    button {
		font-family: "Quicksand", cursive;
	}
    p {
    font-family: 'Hurricane', cursive; 
    }
    :global body {
  background-color: lightblue;
  padding: 2%;
}
</style>
