<script>
    import { onMount } from "svelte";
    let days = ['Sunday','Monday','Tuesday','Wednesday','Thursday','Friday','Saturday'];
    let lastDayOfTheYear = new Date(new Date().getFullYear(), 11, 31);
    let Time = lastDayOfTheYear.getTime() - new Date().getTime();
    let numberOfDaysLeft = Math.round(Time / (1000 * 3600 * 24)); //Diference in Days
    let now = new Date(),
        month,
        day,
        year, today;

    let dateString;
    console.log(now)
    onMount(() => {
        (month = "" + (now.getMonth() + 1)),
            (day = "" + now.getDate()),
            (year = now.getFullYear()),
            (today = "" + days[now.getDay()]);

        if (month.length < 2) month = "0" + month;
        if (day.length < 2) day = "0" + day;

        dateString = [today,day, month, year].join("-");
    });
</script>
<div>
    <h4>Today's Date: {dateString}</h4>
    <h2>There are <span class="highlight">{numberOfDaysLeft}</span> days left in {year}</h2>
</div>


<style type="text/scss">
	@import "../styles.scss";
</style>
