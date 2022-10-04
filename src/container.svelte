<script>
    import { onMount } from "svelte";

    const daysString = [
        "Sunday",
        "Monday",
        "Tuesday",
        "Wednesday",
        "Thursday",
        "Friday",
        "Saturday",
    ];
    const monthString = [
        "January",
        "February",
        "March",
        "April",
        "May",
        "June",
        "July",
        "August",
        "September",
        "October",
        "November",
        "December",
    ];

    let lastDayOfTheYear = new Date(new Date().getFullYear(), 11, 31);
    let Time = lastDayOfTheYear.getTime() - new Date().getTime(); //Diference in Time
    let numberOfDaysLeft = Math.round(Time / (1000 * 3600 * 24)); //Diference in Days
    let weeksLeft = weeksBetween(lastDayOfTheYear);
    let monthsLeft = monthDifference(lastDayOfTheYear);
    let now = new Date(),
        month,
        day,
        year,
        today;

    let dateString;

    onMount(() => {
        (month = "" + monthString[now.getMonth()]),
            (day = "" + now.getDate()),
            (year = now.getFullYear()),
            (today = "" + daysString[now.getDay()]);

        if (month.length < 2) month = "0" + month;
        if (day.length < 2) day = "0" + day;

        dateString = [today, day, month, year].join(" ");
    });

    function weeksBetween(d1, d2 = new Date()) {
        return Math.round((d1 - d2) / (7 * 24 * 60 * 60 * 1000));
    }

    function monthDifference(d1, d2 = new Date()) {
        var months;
        months = (d1.getFullYear() - d1.getFullYear()) * 12;
        months -= d2.getMonth();
        months += d1.getMonth();
        return months <= 0 ? 0 : months;
    }
</script>

<div>
    <h4>Today's Date: {dateString}</h4>
    <h2>
        There are <span class="highlight">{numberOfDaysLeft}</span> days left in {year}
    </h2>
    <p>That leaves us with <b>{weeksLeft}</b> weeks left in the year and <b>{monthsLeft + 1}</b> Months left</p>
</div>

<style type="text/scss">
    @import "../styles.scss";
</style>
